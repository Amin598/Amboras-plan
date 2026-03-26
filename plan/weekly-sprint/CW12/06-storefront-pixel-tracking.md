# PRD: Storefront Pixel & Tracking

## 1. What & Why

Every store needs tracking from day one — merchants need to know where their traffic comes from and how customers behave. We auto-inject Google Analytics 4 and Meta Pixel into every storefront so merchants just enter their pixel IDs and tracking works. No apps, no code, no setup friction.

## 2. What It Must Do

- **Google Analytics 4 (GA4):** auto-injected into every storefront via script tag
- **Meta Pixel (Facebook):** auto-injected into every storefront via script tag
- **Event tracking** — fire standard e-commerce events:
  - `page_view` — every page load
  - `view_item` — product page visit
  - `add_to_cart` — item added to cart
  - `begin_checkout` — checkout started
  - `purchase` — order completed (with value, currency, items)
- **Configuration:** merchant enters GA4 Measurement ID and Meta Pixel ID in store settings (Medusa admin)
- Pixels only load if IDs are configured (no empty script tags)
- Events follow GA4 and Meta's standard e-commerce event schemas

## 3. Conditions & Requirements

- Depends on PRD #05 (storefront template) being built
- Pixel IDs stored as store-level settings/metadata in Medusa
- Script injection must not hurt page load performance (async loading)
- Events must fire correctly on client-side navigation (Next.js SPA behavior)
- Consider: server-side tracking (Conversions API for Meta) — not for MVP, but keep architecture open for it
- Test with GA4 DebugView and Meta Pixel Helper to verify events
