# Amboras MVP Sprint — CW12

Goal: Get the Amboras MVP running end-to-end — a merchant can sign up, have a store provisioned, see their storefront, manage orders via Stripe, and view basic analytics.

---

## 1. Architecture & Infrastructure

### 1.1 Basic Architecture — User Machine & DB

Set up the orchestrator platform and per-store machine infrastructure as defined in Architecture-mvp-v1.md (Option B: Multi-Process).

**How it works — 4 programs total:**

```
amboras.com — landing page, pricing, login/signup
│   After login → redirect to admin.amboras.com
│
admin.amboras.com — WHERE THE MERCHANT WORKS
│   Medusa's admin UI, customized & rebranded for Amboras
│   - Products, orders, customers, analytics — all from Medusa admin
│   - AI chat panel added on top
│   - Unnecessary tabs hidden (price lists, B2B, etc.)
│   - Amboras branding, not Medusa branding
│   Same pattern as Shopify: shopify.com → admin.shopify.com
│
├── Backend API (Node.js/NestJS)
│   - User management, store provisioning, billing, deployment orchestration
├── Supabase (Orchestrator DB) — users, stores, deployments
└── Redis — job queues, caching (native to Medusa, no extra setup)

STORE MACHINE (one per store on Fly.io) — backend services, not directly accessed
├── Process 1: Medusa backend (port 9000)  ← shop engine API (products, orders, customers)
├── Process 2: Next.js storefront (port 3000)  ← what customers see when shopping (only public-facing part)
└── Process 3: AI service (port 8000)  ← AI brain (Claude API, chat, product generation etc.)
    Each with:
    ├── Supabase — products, orders, customers, carts
    ├── Redis — session cache, API cache (native to Medusa) (check how it works with s)
    └── Process manager (pm2 or supervisor) to run all 3 processes on one machine
```

**Flow:** Merchant visits amboras.com → logs in → redirected to admin.amboras.com (Medusa admin, rebranded & customized for Amboras). From there they manage products, orders, customers, chat with AI — all within the customized Medusa admin. Customers visit the storefront (port 3000) — that's the only public-facing part per store.

- **Store provisioning flow**
  - User signs up → orchestrator creates a Fly.io machine → seeds Medusa DB → store is live
  - Connect store machine to orchestrator DB (store record, user ownership)

### 1.2 GitHub Work Structure

Set up the git-based deployment pipeline:

- **Template repo:** `amboras-stores/store-template` — base Medusa + Next.js storefront that every new store forks from (adds version controll)
- **Per-store repos:** `amboras-stores/store-{id}` — forked from template on store creation
- **Branch strategy:** `staging` (auto-deploy) → `main` (manual deploy to production) 
- **GitHub webhooks** → orchestrator → triggers Fly.io machine deployment
- **Deploy flow:** git push → webhook → orchestrator queues job → Fly.io machine pulls latest → build → health check → live

---

## 2. Online Store Tab

### 2.1 Store Overview Page

- Dashboard page showing all stores belonging to the logged-in user
- Fetch all stores related to user from orchestrator DB
- Each store card shows: store name, domain, status (live/staging/down), preview thumbnail
- Click into a store → opens the store management view

### 2.2 Storefront Template — E-commerce Ready

Make the base Next.js + Medusa storefront production-ready out of the box:

- **Pixel & tracking integration**
  - Google Analytics 4 (GA4) snippet — auto-injected per store
  - Meta Pixel (Facebook) — auto-injected per store
  - Custom event tracking: page view, add to cart, begin checkout, purchase
  - Tracking config stored in store settings (merchant enters their pixel IDs)

- **Auto checkout integration (Stripe behind the scenes)**
  - Every store gets checkout wired up automatically — Stripe is invisible to the merchant
  - Checkout flow: cart → Amboras checkout → payment → order created in Medusa
  - No setup needed — Stripe account auto-provisioned on store creation

### 2.3 AI Chat Panel (inside Medusa Admin)

- Add a chat/AI panel into the customized Medusa admin (admin.amboras.com)
- AI chat interface: text input, message history, AI responses with actions (product creation, content generation, store changes)
- AI service (port 8000 on store machine) connects to Claude API, has access to Medusa API, can read/write products, pages, and theme code
- Design should match the Ecomcoder experience — chat-first, action-oriented

### 2.4 GitHub Infrastructure Per Store

- On store creation: fork template repo → create `dev`, `staging`, `main` branches → connect webhook to orchestrator
- Store management UI shows: current deployed commit, branch status, deploy button
- AI changes are committed to git (same pattern as Ecomcoder)

---

## 3. Stripe Integration

### 3.1 Stripe Integration Setup (Invisible to Merchant)

- **Stripe Connect Express** — Amboras auto-provisions a Stripe account per store on creation. Merchant never sees or touches Stripe.
- No OAuth flow, no "Connect Stripe" button — fully automatic behind the scenes
- Bank account / payout details collected during Amboras signup (not via Stripe UI)
- Platform takes a percentage via Stripe Connect application fees (Amboras revenue model)
- Merchant sees: orders, revenue, refunds — all in Amboras admin. Never sees Stripe branding.

### 3.2 Stripe API Integration

Map out and implement the full Stripe API surface we need:

- **Checkout:** Create Checkout Sessions from cart data (products, quantities, shipping)
- **Orders:** On successful payment → create order in Medusa + store in orders DB table + link to customer DB table
- **Refunds:** Stripe Refunds API — merchant can refund from admin dashboard, syncs to Medusa order status
- **Disputes/chargebacks:** Webhook listener for dispute events → notify merchant
- **Subscriptions** (if needed later): Stripe Billing for recurring products
- **Webhooks:** `checkout.session.completed`, `charge.refunded`, `charge.dispute.created`, `payment_intent.succeeded`

### 3.3 Order & Customer Data Flow

- Every successful Stripe payment creates:
  1. An entry in the **orders** DB table (order details, amount, status, Stripe payment ID)
  2. An entry or update in the **customers** DB table (email, name, order history, lifetime value)
- Orders page in admin dashboard pulls from orders table + enriches with Stripe data
- Customer page in admin dashboard shows order history, total spend, contact info

---

## 4. Analytics Dashboard 

### 4.1 Build with Own DB

- Analytics data stored in orchestrator DB (not dependent on third-party analytics tools)
- **Stripe data feed:** daily revenue, orders count, average order value, refund rate — pulled from Stripe API + webhooks
- **Store metrics:** total products, active products, inventory levels
- **Customer metrics:** new vs returning, total customers, top customers by spend

### 4.2 Pixel & Tracking Data

- Use the pixel/tracking data from the storefront (GA4, Meta Pixel events)
- Store-side event collector: page views, add-to-cart events, checkout starts, purchases
- Events stored in analytics tables → power the dashboard
- Key metrics: conversion rate, cart abandonment rate, traffic sources, top pages

### 4.3 Dashboard UI

- Add Analytics page to sidebar navigation
- Dashboard cards: revenue (today/week/month), orders, conversion rate, average order value
- Charts: revenue over time, orders over time, traffic sources
- Tables: recent orders, top products, top customers

---

## 5. Cleanup & Hide 

### 5.1 Hide Unnecessary Tabs

- Remove or hide tabs/sections not relevant to the Amboras use case:
  - **Price lists** — not needed (B2C focused, not B2B wholesale)
  - **Inventory management** (global) — not needed as a standalone section
- Keep the admin clean and focused on what matters: products, orders, customers, analytics

### 5.2 Enable Inventory Per Product

- Inventory tracking stays enabled at the **product level** (stock count per variant)
- Merchant can set stock quantity when creating/editing a product
- Low stock alerts in the dashboard
- But no standalone inventory management section — it lives on the product

### 5.3 Clean Up Product Features

- Remove unnecessary product fields from the creation/edit UI:
  - Harmonized System (HS) codes
  - Mid codes
  - Weight/dimensions (unless shipping is in MVP)
  - Sales channels (there's only one storefront)
  - Collection management (simplify to tags only for MVP)
- Keep it simple: title, description, images, price, variants, stock, tags
- AI product creation handles the heavy lifting anyway — the form is just for review/tweaks

---

## 6. Auto Store Hosting (Requires Research)

Every store is automatically hosted on a subdomain: `{storename}.myamboras.com`. When a merchant creates a store, it's instantly live — no DNS setup, no hosting configuration, no waiting.

- Auto-assign subdomain `{storename}.myamboras.com` on store creation
- Storefront (port 3000 on store machine) served via this subdomain
- SSL/HTTPS automatic for all subdomains
- **Requires research:**
  - How to handle wildcard subdomains on Fly.io (wildcard DNS + wildcard TLS cert)
  - Routing: subdomain → correct store machine
  - Custom domains later (merchant brings their own domain) — not MVP, but architecture should support it
  - CDN/caching layer in front of storefronts

This is the last task of the sprint — needs more thinking before implementation.

---

Sprint Breakdown

 — Foundation

| Day | Focus | Tasks |
|---|---|---|
| Mon–Tue | Infrastructure | Orchestrator backend + DB schema, Fly.io machine provisioning, store creation flow |
| Wed | Git & Deploy | Template repo, per-store forking, webhook → deploy pipeline |
| Thu | Stripe | Auto Stripe provisioning on store creation, checkout session creation, webhook listeners |
| Fri | Frontend | Admin dashboard layout, store overview page, sidebar navigation |

Features & Polish

| Day | Focus | Tasks |
|---|---|---|
| Mon | Storefront | Template storefront production-ready, pixel/tracking, Stripe checkout wired |
| Tue | AI Interface | Chat area UI, AI service integration, Claude API connection |
| Wed | Orders & Customers | Order creation from Stripe webhooks, customer table, admin order/customer pages |
| Thu | Analytics | Analytics DB tables, Stripe data feed, dashboard UI with charts |
| Fri | Cleanup | Hide unnecessary tabs, clean product fields, inventory per product, QA pass |

---

## Dependencies & Risks

- **Stripe Connect platform approval** — need to apply for Stripe Connect platform access; may take a few days
- **Fly.io machine provisioning** — need to test machine creation time and cold start performance
- **Medusa customization depth** — need to verify which admin features can be hidden vs need custom UI
- **Template storefront quality** — the base template needs to look professional out of the box; may need design time
