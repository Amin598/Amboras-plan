# PRD: Auto Store Hosting

**Status: Requires Research**

## 1. What & Why

Every store needs to be live instantly on creation. We auto-host every store on a subdomain: `{storename}.myamboras.com`. No DNS setup, no hosting config, no waiting. Merchant creates store → it's live.

This requires research before full implementation.

## 2. What It Must Do

- Auto-assign subdomain `{storename}.myamboras.com` on store creation
- Storefront (port 3000 on store machine) served via this subdomain
- SSL/HTTPS automatic for all subdomains
- Subdomain routing: request to `{storename}.myamboras.com` → correct store's Fly.io machine

## 3. Conditions & Requirements

**Requires research:**
- How to handle wildcard subdomains on Fly.io (wildcard DNS + wildcard TLS cert)
- Routing layer: how does a request to a subdomain find the right store machine?
- Custom domains later (merchant brings own domain) — not MVP, but architecture must support it
- CDN/caching layer in front of storefronts — needed for performance?
- Subdomain validation: what names are allowed, reserved names, conflicts
