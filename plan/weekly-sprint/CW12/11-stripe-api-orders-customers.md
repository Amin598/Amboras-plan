# PRD: Stripe API, Orders & Customers

## 1. What & Why

Stripe is our payment API layer — it handles checkout, refunds, and disputes. But all data (orders, customers) lives in Medusa's own database. Stripe is the pipe, not the source of truth. The merchant never interacts with Stripe — Amboras manages all payment operations internally. If we ever want to swap Stripe, we just change the payment layer — all data stays untouched.

Key principle: **Stripe manages payments, Medusa DB owns the data. Stripe is invisible to the merchant.**

## 2. What It Must Do

**Stripe API integrations (all handled by Amboras internally):**
- **Checkout Sessions:** create Stripe Checkout Sessions from Medusa cart data (products, quantities, shipping, store's auto-provisioned Stripe account)
- **Refunds:** merchant clicks refund in admin → Amboras calls Stripe Refunds API → order status updated in Medusa DB (merchant never sees Stripe)
- **Disputes/chargebacks:** Amboras reads dispute data from Stripe, displays in admin as an Amboras notification

**Webhook listeners:**
- `checkout.session.completed` → create order in Medusa DB + create/update customer in Medusa DB
- `charge.refunded` → update order status to refunded in Medusa DB
- `charge.dispute.created` → notify merchant via Amboras admin, flag order
- `payment_intent.succeeded` → confirm payment received
- `account.updated` → Stripe account status changes (handled internally)

**Webhook infrastructure:**
- Webhook endpoint on orchestrator backend
- Signature verification (Stripe webhook secret)
- Idempotency handling (don't process same event twice)
- Failed webhook retry handling

**Order & customer data (stored in Medusa DB, not Stripe):**
- Every successful payment creates an order in Medusa: items, quantities, prices, payment status, Stripe payment ID, customer info, order status
- Every new customer gets a record in Medusa: email, name, address, order history, lifetime value
- Repeat purchases link to existing customer record
- Orders page in admin: list, filter, detail, refund button
- Customers page in admin: list, filter, detail with order history and total spend

## 3. Conditions & Requirements

- Depends on PRD: Stripe Integration Setup for auto-provisioned Stripe accounts
- Medusa already has orders and customers tables — we use them as-is, Stripe just feeds data into them
- Medusa has a built-in Stripe plugin — check what it covers vs what we need custom
- Stripe webhook → Medusa order creation must be reliable (idempotent, retry-safe)
- Webhook endpoint must be publicly accessible
- All Stripe interactions are internal — merchant never sees Stripe references in the UI
- Architecture must make Stripe swappable — no Stripe-specific logic in order/customer data models
