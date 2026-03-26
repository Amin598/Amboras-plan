# PRD: Medusa Admin Rebrand

## 1. What & Why

We use Medusa's admin dashboard as our merchant-facing admin (admin.amboras.com), but it needs to look and feel like Amboras — not like default Medusa. We rebrand it, hide unnecessary B2B features, and clean up the product creation flow so it's simple and focused on what B2C merchants actually need.

## 2. What It Must Do

**Rebrand:**
- Replace Medusa logo/branding with Amboras branding throughout the admin
- Custom color scheme matching Amboras brand
- Update page titles, favicons, loading screens

**Hide unnecessary tabs/sections:**
- Price lists — not needed (B2C, not B2B wholesale)
- Inventory management as standalone section — not needed
- Gift cards (not in MVP)
- Transfer/purchase orders — B2B feature
- Sales channels (there's only one storefront)
- Keep admin focused on: Products, Orders, Customers, Analytics, Settings

**Clean up product features:**
- Hide unnecessary product fields:
  - Harmonized System (HS) codes
  - Mid codes
  - Weight/dimensions (unless shipping needs it)
  - Collection management (simplify to tags only for MVP)
- Keep it simple: title, description, images, price, variants, stock, tags

**Enable inventory per product:**
- Stock count per variant on the product edit page
- Low stock indicator
- No standalone inventory section — it lives on the product

## 3. Conditions & Requirements

- Medusa admin is a React app — need to understand its customization/extension points
- Check if Medusa supports admin UI plugins or if we need to fork the admin
- Changes must survive Medusa upgrades — prefer configuration over code changes where possible
- Sidebar navigation must be customizable (show/hide menu items)
- Product form must be customizable (show/hide fields)
- Test that hiding features doesn't break underlying Medusa functionality
