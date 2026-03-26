# Built-In Domain Search & Hosting

## The Problem

Setting up a store on Shopify (or anywhere else) means dealing with multiple services just to get online:

- **Domain registration** — Go to GoDaddy, Namecheap, or another registrar. Search for domains, compare pricing, buy one.
- **DNS configuration** — Point your domain to your store. Edit A records, CNAMEs, nameservers. Most merchants have no idea what any of this means.
- **Hosting** — Shopify handles this, but if you're on WooCommerce or another self-hosted platform, you need a separate hosting provider (Vercel, Netlify, AWS, shared hosting). Pick a plan, configure it, deploy.
- **SSL certificates** — Make sure HTTPS works. Some platforms handle it, others make you deal with Let's Encrypt or paid certs.
- **Email setup** — Want a branded email (hello@yourstore.com)? That's yet another service to configure.

This is a mess for non-technical merchants. Even on Shopify, buying a domain through their interface is clunky and overpriced, and connecting an external domain requires DNS knowledge.

## The Amboras Approach

Amboras owns the full stack from domain to deployment. There is no "connect your hosting" step. There is no DNS to configure. The merchant never leaves Amboras.

### Domain Search & Registration

- **Search directly in Amboras** — Merchant types in their desired store name, Amboras shows available domains (.com, .de, .shop, .store, etc.) with pricing.
- **One-click purchase** — Buy the domain right there. No redirect to a registrar, no account to create elsewhere.
- **AI domain suggestions** — If the desired domain is taken, AI suggests alternatives based on the store name, niche, and target market. Not just random appended words — actually good suggestions.
- **Domain management** — Renewals, transfers, DNS records (for advanced users) — all managed inside Amboras. No separate registrar dashboard.

### Hosting — Zero Configuration

- **Every store is hosted by Amboras** — There is no hosting step. You create a store, it's live. Period.
- **No server selection, no plan tiers for hosting** — Hosting is part of the platform, not an upsell.
- **Global CDN** — Store assets served from edge locations worldwide. Fast load times everywhere, automatically.
- **Auto-scaling** — Traffic spike from a viral product or ad campaign? Infrastructure handles it. Merchant never thinks about servers.
- **SSL/HTTPS** — Automatic for every store, every custom domain. No setup, no renewal.

### Subdomains for Getting Started

- **Instant store URL** — Every store gets a `yourstore.amboras.com` subdomain immediately on signup. Store is live before the merchant even thinks about a custom domain.
- **Upgrade to custom domain anytime** — Seamless switch from subdomain to custom domain with zero downtime. No re-configuration, no broken links.

### Branded Email (Future)

- **yourname@yourstore.com** — Offer branded email as part of the domain package. One less service to set up.

## Why This Matters

- **Removes a massive friction point** — Domain + hosting setup is where non-technical merchants get stuck or give up entirely. Removing it means faster time-to-live.
- **Keeps everything in one place** — No context-switching between registrar, hosting provider, and store admin. One dashboard, one bill.
- **Revenue opportunity** — Domain registration and premium hosting tiers are a recurring revenue stream.
- **Competitive edge** — Shopify does sell domains, but at inflated prices ($14+/year), with limited TLD options, clunky DNS management, and a mediocre UX. WooCommerce requires full self-hosting. Amboras beats both by offering at-cost domain pricing, AI-powered suggestions, and truly zero-config setup where the merchant never touches DNS.
- **Supports the "we do the work" thesis** — A merchant who can't configure DNS shouldn't need to. Amboras handles it so they can focus on selling.

## Technical Considerations

- Need a domain registrar API integration (e.g., Namecheap API, Cloudflare Registrar, or a reseller like OpenSRS/Enom)
- DNS managed via Cloudflare or similar — automatic record creation when a domain is connected
- Wildcard SSL via Let's Encrypt or Cloudflare for all custom domains
- Store hosting is already part of the platform architecture — this feature is about making the domain side equally seamless
- Consider Cloudflare Registrar for at-cost domain pricing as a competitive advantage
