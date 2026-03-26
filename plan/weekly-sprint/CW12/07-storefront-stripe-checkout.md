# PRD: Storefront Checkout

## 1. What & Why

Every store needs a working checkout from day one. Checkout is powered by Stripe behind the scenes but the merchant and customer never know — it's an Amboras-branded checkout experience. Cart → payment → order confirmed. Works automatically from the moment a store is created.

## 2. What It Must Do

- Checkout flow in the storefront: cart → enter shipping info → payment → order confirmation page
- Create Stripe Checkout Sessions from cart data (products, quantities, shipping cost) — using the auto-provisioned Stripe account for that store
- On successful payment: create order in Medusa, redirect customer to confirmation page
- On failed payment: show error, let customer retry
- Support standard payment methods: credit/debit cards (Stripe handles Apple Pay, Google Pay automatically)
- Order confirmation page shows: order number, items, total, estimated delivery
- Checkout is Amboras-branded — no Stripe branding visible to customer or merchant

## 3. Conditions & Requirements

- Depends on PRD: Storefront Template Build for the checkout UI
- Depends on PRD: Stripe Integration Setup for the auto-provisioned Stripe account
- Medusa has built-in Stripe plugin — use it, don't build custom
- Checkout must work on mobile
- Handle edge cases: expired cart, out-of-stock items, Stripe downtime
- PCI compliance: we never touch card data — Stripe Checkout handles it
- Consider shipping calculation: flat rate for MVP or real-time rates later
