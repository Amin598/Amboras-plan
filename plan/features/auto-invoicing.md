# Auto Invoice Generation

## Status: idea

## What & Why

Every e-commerce order needs a legally compliant invoice. In Germany/EU this is a hard legal requirement — every Rechnung must have a sequential invoice number, merchant's Steuernummer or USt-IdNr, correct VAT rate and amount, full addresses, date, and line item breakdown.

Shopify deliberately doesn't do this. Their "invoices" are just order confirmations that aren't legally compliant in most EU countries. German Shopify merchants are forced to buy third-party apps (Suffio, Billbee, sevDesk) just to generate proper invoices. It's one of the most common complaints.

Shopify avoids this because tax law differs per country and getting it wrong creates legal liability. They punt the problem to app developers.

Amboras takes the middle ground: we auto-generate invoices based on the merchant's store data and order details, but **we don't take responsibility for tax correctness**. The merchant is always responsible for reviewing and ensuring their invoices are legally compliant. Clear disclaimer in the UI and in our terms of service. This removes the liability risk that scares Shopify off, while still solving the pain point — the merchant gets a ready-made invoice instead of nothing, they just need to double-check it.

## What It Must Do

- Auto-generate a legally compliant invoice (Rechnung) for every completed order
- Include all legally required fields for German/EU invoices:
  - Sequential invoice number (Rechnungsnummer)
  - Invoice date
  - Merchant's full name/company and address
  - Merchant's Steuernummer or USt-IdNr
  - Customer's full name and address
  - Line items with quantity, unit price, total
  - VAT rate and VAT amount per line item
  - Net total, VAT total, gross total
  - Payment method reference
- Attach invoice PDF to the order in the admin dashboard
- Auto-send invoice to customer via email on order completion
- Merchant can download any invoice from the admin
- Customer can download their invoice from the order confirmation page
- Support for credit notes (Gutschrift/Stornorechnung) on refunds

## Conditions & Requirements

- Merchant must provide their tax ID (Steuernummer or USt-IdNr) during store setup
- Need to determine correct VAT rates per country (19% DE, 20% AT, etc.) — Stripe Tax could feed this
- Invoice numbering must be sequential and gap-free (German tax law requirement)
- PDF generation needed (server-side, per order)
- Start with Germany, then expand to EU countries
- Research: legal requirements per target country — what fields are mandatory
- Research: Kleinunternehmerregelung (small business exemption, §19 UStG) — these merchants don't charge VAT, invoices must explicitly state the exemption
- Consider: integration with accounting tools (sevDesk, lexoffice, DATEV) as a later add-on
