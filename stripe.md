# Stripe Integration Plan

## Overview

Amboras uses **Stripe Connect with Direct Charges**. All money flows directly through the merchant's Stripe account — Amboras never holds funds. We're just the UI layer on top of Stripe. Merchants manage everything (orders, refunds, payouts) through the Amboras admin, but behind the scenes it's all Stripe API calls hitting their connected account.

**Core principle:** Stripe manages the money. Amboras manages the experience.

---

## Architecture

```
Customer visits storefront → clicks checkout
    → Amboras creates Stripe Checkout Session (direct charge on merchant's account)
    → funds go DIRECTLY to merchant's Stripe account
    → Stripe auto-deducts application fee (Amboras revenue)
    → Stripe auto-deducts processing fees
    → merchant gets the rest → Stripe pays out to their bank

Amboras never touches the money. Ever.

Merchant sees in Amboras admin:
    → Orders (fetched from merchant's Stripe account via API)
    → Revenue & payouts (fetched from merchant's Stripe account via API)
    → Refund button (creates refund on merchant's Stripe account via API)
    → Dispute notifications (from Stripe webhooks)
```

---

## 1. Connected Account Creation (per store)

When a merchant creates a store on Amboras, we auto-create a Stripe connected account.

> Express accounts are deprecated. Use controller properties (Accounts v2).

```js
const account = await stripe.accounts.create({
  controller: {
    fees: { payer: 'account' },              // MERCHANT pays Stripe processing fees
    losses: { payments: 'stripe' },          // Stripe handles dispute losses (default behavior)
    stripe_dashboard: { type: 'none' },      // Merchant never sees Stripe dashboard
  },
  country: 'DE',
  email: merchant.email,
  business_type: 'individual',
});

// Store account.id (acct_xxx) in orchestrator DB → linked to store
```

**Controller properties:**

| Property | Value | What it means |
|---|---|---|
| `fees.payer` | `account` | Merchant pays Stripe's processing fees (2.9% + 30¢) — standard |
| `losses.payments` | `stripe` | Stripe's default dispute handling — we don't get involved in chargebacks |
| `stripe_dashboard.type` | `none` | Merchant never sees Stripe — fully white-labeled through Amboras |

**DB schema:**

```sql
ALTER TABLE stores ADD COLUMN stripe_account_id TEXT;
ALTER TABLE stores ADD COLUMN stripe_onboarding_complete BOOLEAN DEFAULT FALSE;
ALTER TABLE stores ADD COLUMN stripe_charges_enabled BOOLEAN DEFAULT FALSE;
ALTER TABLE stores ADD COLUMN stripe_payouts_enabled BOOLEAN DEFAULT FALSE;
```

---

## 2. Merchant Onboarding (KYC)

Stripe legally must verify the merchant (identity + bank account). Can't skip this.

### MVP: Stripe-hosted onboarding

```js
const accountLink = await stripe.accountLinks.create({
  account: 'acct_xxx',
  refresh_url: 'https://admin.amboras.com/onboarding/refresh',
  return_url: 'https://admin.amboras.com/onboarding/complete',
  type: 'account_onboarding',
});
// redirect merchant to accountLink.url
```

**Flow:**

```
Merchant signs up on Amboras
  → We create Stripe connected account (instant, API call)
  → Redirect to Stripe-hosted onboarding page
  → Merchant enters: legal name, DOB, address, ID document, bank account
  → Takes 2-3 minutes
  → Redirects back to Amboras admin
  → We listen for account.updated webhook → mark store as payment-ready
  → Done. Store can accept payments.
```

Post-MVP: embed Stripe's onboarding components in our own UI for a seamless experience.

---

## 3. Checkout Flow (Direct Charges)

Customer buys something → we create a Stripe Checkout Session as a **direct charge on the merchant's connected account**. Money goes straight to them.

**Why direct charges:**

- Amboras **never holds funds** — zero financial liability
- Money goes directly to merchant's Stripe balance
- Stripe handles payouts to merchant's bank automatically
- Amboras just takes an application fee (auto-deducted by Stripe)
- Way simpler for an MVP — no fund management, no transfers, no reversals

```js
const session = await stripe.checkout.sessions.create(
  {
    mode: 'payment',
    line_items: cart.items.map(item => ({
      price_data: {
        currency: 'eur',
        product_data: {
          name: item.name,
          images: [item.image],
        },
        unit_amount: item.price, // in cents
      },
      quantity: item.quantity,
    })),
    payment_intent_data: {
      application_fee_amount: calculateFee(cart.total), // Amboras takes its cut
    },
    success_url: `${storefrontUrl}/order/confirmation?session_id={CHECKOUT_SESSION_ID}`,
    cancel_url: `${storefrontUrl}/cart`,
    customer_email: customer.email,
    shipping_address_collection: {
      allowed_countries: ['DE', 'AT', 'CH', 'US', 'GB', 'FR', 'NL'],
    },
  },
  {
    stripeAccount: store.stripe_account_id, // Direct charge on merchant's account
  }
);
```

**Key difference from destination charges:** the second argument `{ stripeAccount: ... }` makes this a direct charge. The payment is created ON the merchant's account, not on ours. We never see the funds.

**Fee calculation:**

```js
function calculateFee(totalInCents) {
  // Amboras takes 3% of every transaction
  return Math.round(totalInCents * 0.03);
}
// On a €100 order: merchant gets €100 - €2.90 (Stripe fee) - €3.00 (Amboras fee) = €94.10
// Amboras receives €3.00 in application fees (deposited to our platform Stripe account)
```

---

## 4. Fetching Orders & Payments (Admin Dashboard)

Merchant sees orders in Amboras admin. We fetch from their Stripe account using the `stripeAccount` header.

```js
// List all payments for this store
const payments = await stripe.paymentIntents.list(
  { limit: 20, expand: ['data.latest_charge'] },
  { stripeAccount: store.stripe_account_id }
);

// Get a specific payment with full details
const payment = await stripe.paymentIntents.retrieve(
  'pi_xxx',
  { expand: ['latest_charge', 'latest_charge.balance_transaction'] },
  { stripeAccount: store.stripe_account_id }
);

// List charges (includes refund status)
const charges = await stripe.charges.list(
  { limit: 20 },
  { stripeAccount: store.stripe_account_id }
);

// Get checkout session details (line items, customer info, shipping)
const session = await stripe.checkout.sessions.retrieve(
  'cs_xxx',
  { expand: ['line_items', 'customer_details'] },
  { stripeAccount: store.stripe_account_id }
);
```

**What you get from each payment:**
- Amount, currency, status (succeeded/failed/refunded)
- Customer email, name, shipping address
- Line items (what they bought)
- Payment method (card brand, last 4 digits)
- Created timestamp
- Refund status and amount

**Important with direct charges:** payments only exist on the merchant's connected account, NOT on the Amboras platform account. You must always pass `{ stripeAccount: ... }` to see them.

---

## 5. Refunds

Merchant clicks "Refund" in Amboras admin → we call Stripe on their connected account.

```js
// Full refund
const refund = await stripe.refunds.create(
  { payment_intent: 'pi_xxx' },
  { stripeAccount: store.stripe_account_id }
);

// Partial refund
const refund = await stripe.refunds.create(
  {
    payment_intent: 'pi_xxx',
    amount: 1500, // refund €15.00
  },
  { stripeAccount: store.stripe_account_id }
);
```

**With direct charges, refunds are simple:**
- Refund is debited from the **merchant's Stripe balance** — not ours
- Amboras doesn't need to manage any fund transfers or reversals
- Application fee is NOT automatically refunded — we keep our cut by default
- To also refund the application fee: `refund_application_fee: true`

```js
// Refund AND give back Amboras's fee
const refund = await stripe.refunds.create(
  {
    payment_intent: 'pi_xxx',
    refund_application_fee: true, // Amboras gives back its cut too
  },
  { stripeAccount: store.stripe_account_id }
);
```

---

## 6. Webhooks

Stripe sends events to our endpoint when things happen on connected accounts.

**Endpoint:** `POST https://api.amboras.com/webhooks/stripe`

**Register for Connect webhooks** (events on connected accounts, not our platform account):

| Event | What to do |
|---|---|
| `checkout.session.completed` | Store order data in our DB (for fast lookups), send confirmation email |
| `payment_intent.succeeded` | Backup confirmation — payment went through |
| `charge.refunded` | Update order status in our DB, notify merchant |
| `charge.dispute.created` | Notify merchant in admin — "Order #123 disputed" |
| `charge.dispute.closed` | Update dispute status (won/lost) |
| `account.updated` | Check if onboarding complete, update store status in DB |
| `payout.paid` | Show in merchant's payout history |
| `payout.failed` | Alert merchant — bank details may be wrong |

```js
app.post('/webhooks/stripe', express.raw({ type: 'application/json' }), (req, res) => {
  const sig = req.headers['stripe-signature'];
  const event = stripe.webhooks.constructEvent(req.body, sig, WEBHOOK_SECRET);

  // For Connect webhooks, event.account contains the connected account ID
  const connectedAccountId = event.account;

  switch (event.type) {
    case 'checkout.session.completed': {
      const session = event.data.object;
      // 1. Find store by connectedAccountId
      // 2. Store order in our DB (session ID, items, total, customer email, status)
      // 3. Send order confirmation email to customer
      // 4. Decrement inventory in Medusa
      break;
    }
    case 'charge.refunded': {
      const charge = event.data.object;
      // 1. Find order in our DB by charge/payment_intent ID
      // 2. Update status → 'refunded' or 'partially_refunded'
      break;
    }
    case 'charge.dispute.created': {
      const dispute = event.data.object;
      // 1. Find order, flag as disputed
      // 2. Notify merchant in admin
      break;
    }
    case 'account.updated': {
      const account = event.data.object;
      // 1. Update store: charges_enabled, payouts_enabled
      // 2. If both true → store is ready to accept payments
      break;
    }
  }

  res.json({ received: true });
});
```

**Important:**
- Use **Connect webhook endpoint** (not regular) — so you receive events from connected accounts
- Verify webhook signatures always
- Store processed event IDs to prevent double-processing
- Return 200 immediately, process async

---

## 7. Payouts

Stripe automatically pays out from merchant's Stripe balance to their bank account. Default: daily rolling with 2-day delay. Amboras doesn't need to do anything — Stripe handles it.

We can show payout info in the admin:

```js
// List merchant's payouts
const payouts = await stripe.payouts.list(
  { limit: 20 },
  { stripeAccount: store.stripe_account_id }
);

// Each payout shows: amount, status, arrival_date, bank account last 4
```

Optionally let merchant change payout schedule:

```js
await stripe.accounts.update(store.stripe_account_id, {
  settings: {
    payouts: {
      schedule: { interval: 'weekly', weekly_anchor: 'monday' },
    },
  },
});
```

---

## 8. Disputes & Chargebacks

With direct charges + `losses.payments: 'stripe'`:
- Disputes are debited from the **merchant's Stripe balance** (not ours)
- Stripe handles the default dispute process
- We just notify the merchant and optionally help them submit evidence

```js
// Submit dispute evidence on behalf of merchant
await stripe.disputes.update(
  'dp_xxx',
  {
    evidence: {
      customer_email_address: 'customer@example.com',
      shipping_tracking_number: 'TRACK123',
      product_description: 'Blue T-Shirt, Size M',
    },
  },
  { stripeAccount: store.stripe_account_id }
);
```

---

## 9. What Amboras Stores in Its Own DB

Even though Stripe is the source of truth for payments, we store minimal order data for fast lookups:

```sql
CREATE TABLE orders (
  id UUID PRIMARY KEY,
  store_id UUID REFERENCES stores(id),
  stripe_checkout_session_id TEXT,
  stripe_payment_intent_id TEXT,
  customer_email TEXT,
  customer_name TEXT,
  amount_total INTEGER, -- in cents
  currency TEXT,
  status TEXT, -- 'paid', 'refunded', 'partially_refunded', 'disputed'
  items JSONB, -- line items snapshot
  shipping_address JSONB,
  created_at TIMESTAMPTZ DEFAULT NOW()
);
```

This table is populated by webhooks. When merchant wants full details, we fetch from Stripe API. This gives us:
- Fast order listing without hitting Stripe on every page load
- Ability to search/filter orders
- Data for analytics dashboard
- Independence from Stripe API availability

---

## 10. Costs

| Item | Cost | Who pays |
|---|---|---|
| Stripe processing fee | ~2.9% + 30¢ per transaction | Merchant (deducted from their payment) |
| Connected account fee | $2/month per active account | Amboras (platform cost) |
| Payout fee | 0.25% + $0.25 per payout | Merchant (deducted from payout) |
| Dispute fee | $15 per dispute | Merchant (from their balance) |
| Application fee | 3-5% per transaction | Customer pays → Amboras receives |

Amboras's only cost is $2/month per active store. Revenue comes from application fees on every transaction.

---

## 11. Implementation Order

### Phase 1 — Account Setup (Day 1)
1. **Apply for Stripe Connect platform access** — do this FIRST, approval takes 1-3 days
2. Set up Stripe test mode keys in orchestrator env
3. Implement connected account creation on store signup
4. Implement Stripe-hosted onboarding redirect + return flow
5. Implement `account.updated` webhook → track onboarding status

### Phase 2 — Checkout (Day 2)
6. Implement Checkout Session creation (direct charge with `stripeAccount`)
7. Implement `checkout.session.completed` webhook → store order in DB
8. Build order confirmation page on storefront
9. Test full flow: product → cart → checkout → pay → confirmation

### Phase 3 — Orders in Admin (Day 3)
10. Build orders list page — fetch from Stripe API via connected account
11. Build order detail page — payment info, line items, customer, shipping
12. Implement refund button → calls Stripe Refunds API on connected account
13. Build basic revenue/payout view — fetch from Stripe balance API

### Phase 4 — Polish (Day 4)
14. Remaining webhook handlers (refunds, disputes, payouts)
15. Webhook signature verification + idempotency
16. Error states: failed payments, incomplete onboarding, disabled accounts
17. Customers page — aggregate from orders data

---

## Open Decisions

| Decision | Recommendation |
|---|---|
| One Stripe account per store or per merchant? | Per store — simpler, clean separation |
| Application fee % | Start at 3% for MVP, adjust later |
| Refund application fee when merchant refunds? | Yes (`refund_application_fee: true`) — builds trust |
| Shipping rates | Flat rate for MVP |
| Payout schedule default | Daily with 2-day delay (Stripe default) — let merchant change later |
