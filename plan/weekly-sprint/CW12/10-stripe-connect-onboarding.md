# PRD: Stripe Integration Setup

## 1. What & Why

Every store needs to accept payments from day one. Stripe is our payment layer but the merchant never sees or interacts with Stripe directly — Amboras handles everything automatically behind the scenes. When a store is created, we auto-provision a Stripe account for it. The merchant doesn't even know Stripe is involved.

This is also the Amboras revenue model — we take a platform fee on every transaction via Stripe Connect application fees.

## 2. What It Must Do

- **Automatic Stripe provisioning:** when a store is created, Amboras auto-creates a Stripe Connect account for that store — no merchant action needed
- **Stripe Connect type:** Express (Amboras controls the experience, merchant never touches Stripe)
- **Invisible to merchant:** no "Connect Stripe" button, no OAuth flow, no Stripe branding visible anywhere
- **Application fees:** on every transaction, Amboras takes X% via `application_fee_amount` on Checkout Sessions
- **Payouts:** merchant receives payouts to their bank account (collected during signup, not via Stripe UI)
- **Platform manages everything:** refunds, disputes, account status — all handled by Amboras, not the merchant going to Stripe

## 3. Conditions & Requirements

- Need to apply for Stripe Connect platform access (may take a few days for approval)
- Stripe Connect account ID stored in orchestrator DB, linked to store
- Bank account / payout details collected during Amboras signup (not via Stripe's UI)
- Must handle: payout failures, account restrictions
- Merchant never sees Stripe dashboard, Stripe emails, or Stripe branding
- Consider: one Stripe account per store or per merchant?
- PCI compliance: we never store card details — Stripe handles everything
- Test with Stripe test mode before going live
