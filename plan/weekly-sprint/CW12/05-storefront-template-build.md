# PRD: Storefront Template Build

## 1. What & Why

The base storefront template is what every new Amboras store starts with. We take Medusa's default Next.js storefront and rebuild it into a production-ready, conversion-optimized B2C e-commerce template. This needs to look professional out of the box — a merchant should be able to add products and start selling immediately without touching design or code.

This is the first thing customers see. If it looks cheap or broken, no one buys.

## 2. What It Must Do

- Rebuild Medusa's Next.js storefront into a clean, modern B2C e-commerce template
- **Homepage:** hero section, featured products, collections, testimonials section, newsletter signup
- **Product pages:** product images gallery, description, price, variant selector, add to cart, related products
- **Collection/category pages:** product grid with filters (price, category, tags), sorting, pagination
- **Cart:** slide-out cart or cart page, quantity edit, remove items, subtotal, proceed to checkout
- **Checkout flow:** shipping info, payment (Stripe — wired in PRD #07), order confirmation
- **Navigation:** header with logo, menu, search, cart icon, account icon. Footer with links, social, newsletter
- **Mobile-first:** fully responsive, touch-friendly, fast on mobile
- **SEO basics:** proper meta tags, Open Graph, structured data, clean URLs
- **Performance:** fast load times, optimized images, minimal JS bundle

## 3. Conditions & Requirements

- Built on Medusa's Next.js starter — extend, don't start from scratch
- Must connect to Medusa API for all data (products, collections, cart, checkout)
- Design should be neutral/clean enough to work for any product category
- Tailwind CSS for styling
- No custom fonts that slow down loading for MVP — use system fonts or one Google Font
- Template lives in the `amboras-stores/store-template` repo (PRD #03)
- Consider: should the AI be able to modify this template later? (yes — so keep the code clean and well-structured)
