# PRD: Analytics Dashboard

## 1. What & Why

Merchants need to see how their store is performing — revenue, orders, conversion rates, traffic. We build our own analytics dashboard powered by our own DB (Supabase), fed by Stripe data and storefront pixel/tracking events. No dependency on third-party analytics tools for the core dashboard.

This is a key Amboras differentiator: Shopify's analytics are one of the top complaints. Ours should be clear, actionable, and built-in from day one.

## 2. What It Must Do

**Data sources:**
- **Stripe data:** daily revenue, order count, average order value, refund rate — from Stripe API + webhooks
- **Pixel/tracking data:** page views, add-to-cart events, checkout starts, purchases — from storefront event collector
- **Store data:** total products, active products, inventory levels — from Medusa API
- **Customer data:** new vs returning, total customers, top customers by spend — from Medusa/orders DB

**Dashboard UI (new page in Medusa admin sidebar):**
- **Summary cards:** revenue (today/week/month), orders, conversion rate, average order value
- **Charts:** revenue over time, orders over time, traffic sources
- **Tables:** recent orders, top products by revenue, top customers by spend

**Data storage:**
- Analytics events stored in Supabase (orchestrator DB) — separate analytics tables
- Aggregated daily/weekly/monthly summaries for fast dashboard loading
- Store-side event collector sends events to orchestrator API

## 3. Conditions & Requirements

- Depends on PRD #06 (pixel & tracking) for storefront events
- Depends on PRD #11 (Stripe webhooks) for payment data
- Analytics tables in Supabase: events, daily_summaries, traffic_sources
- Event collector must be lightweight — don't slow down the storefront
- Dashboard must load fast — pre-aggregate data, don't query raw events on every page load
- Consider: real-time vs batch processing (batch is fine for MVP — update every 15 min or hourly)
- Privacy: don't store PII in analytics tables — use anonymized/aggregated data
