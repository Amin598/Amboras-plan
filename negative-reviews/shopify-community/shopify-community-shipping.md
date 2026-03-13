# Shopify Community Forum: Shipping Complaints

Source: community.shopify.com — direct merchant complaints about Shopify's shipping features and limitations.

---

## Rate Calculation & Pricing Discrepancies

**1. Multi-package weight calculation failure**
- **User:** Erich3
- **Date:** February 2025
- **Quote:** "Shopify thinks the entire order goes in one huge box... and so I can't use the shipping. Pay 12 months for a service, spend 9 months working on the website, spend $5000... you can't use."
- **Issue:** Products weighing 48 lbs each ordered in quantities of 4 are treated as a single 192 lb shipment, triggering UPS surcharges. No shipping estimates appear when orders exceed 150 lbs combined weight, causing cart abandonment.
- **Thread:** https://community.shopify.com/t/shopify-shipping-is-anyone-listening-to-our-very-basic-needs-please/395886

**2. Dimensional weight ignored for multi-item orders**
- **User:** pokupoku
- **Date:** April 2022, bumped April 2024
- **Quote:** "If someone buys two items with a dimension 16x16x16 inches and 5 pounds each, the shopify will say its a single 16 cubed box weighing 10 pounds."
- **Quote:** "This is embarrassingly incompetent from a company with a market cap of $58,000,000,000."
- **Issue:** Shopify combines weights but not dimensions for multi-item orders. USPS and UPS base rates on package size while Shopify relies solely on weight. Issue remained unresolved for 2+ years.
- **Thread:** https://community.shopify.com/c/shopify-discussions/wrong-shipping-calculated/td-p/1564519

**3. UPS checkout rates vs. label costs — $40 gap**
- **User:** Tim_Akers
- **Date:** November 20, 2024
- **Quote:** "customer being charged $40 and when we print the label it is jumping to $80"
- **Issue:** Ski shipments showing 30-50% rate increases over two weeks. Checkout price and label price dramatically differ.
- **Thread:** https://community.shopify.com/t/ups-shipping-rates-wrong-at-checkout-increase-in-rates/375370

**4. Customer sees $80 shipping, label costs $35**
- **User:** DinDrones
- **Date:** January 8, 2025
- **Quote:** "My customers see 80$ shipping while I buy the label for 35$"
- **Issue:** Severe rate discrepancy in the opposite direction — customers being overcharged and abandoning carts.
- **Thread:** https://community.shopify.com/t/ups-shipping-rates-wrong-at-checkout-increase-in-rates/375370

**5. Long items trigger absurd pricing**
- **User:** dpd11
- **Date:** November 21, 2024
- **Quote:** "48x4x4 3 pounds CA to NY for $13. Just change that to 50" length and it goes to $78"
- **Quote:** "There is literally no phone support whatsoever now, which for a 100 billion $ company is absurd."
- **Issue:** Items over 48 inches showing 2-3x price increases with no explanation or way to fix it.
- **Thread:** https://community.shopify.com/t/ups-shipping-rates-wrong-at-checkout-increase-in-rates/375370

**6. Losing money on every shipment**
- **User:** FandeaFabrics
- **Date:** March 9, 2022 (problem started January 1, 2022)
- **Quote:** "a customer was charged $5.68 and we are being charged $5.96 to ship the package. SAME WEIGHT. We are losing money and I can't get anyone on the phone."
- **Issue:** Shopify's calculated rates systematically undercharge customers compared to what the merchant pays for the label. Shopify support stopped responding after January 20, 2022.
- **Thread:** https://community.shopify.com/c/payments-shipping-and/losing-money-on-shipping-shopify-is-undercharging/m-p/1515904

**7. Customer paid $13, should have been $27**
- **User:** Mkle
- **Date:** April 20, 2022
- **Quote:** "The customer who bought 3 bundles of hair products was only charged $13.00 for shipping... they basically got free shipping for everything else. I had to pay the difference."
- **Issue:** Multi-item orders not multiplying per-item shipping costs correctly.
- **Thread:** https://community.shopify.com/t/why-is-my-shipping-cost-calculation-incorrect-for-multiple-item-orders/115371

**8. USPS label returned for insufficient postage**
- **User:** StitchWitch7
- **Date:** April 27, 2023
- **Quote:** "I had a package returned to me for insufficient postage, and I can't seem to fix my shipping settings so that I pay for the label what USPS says it's supposed to cost."
- **Issue:** USPS charges $5.10, Shopify charges $3.90 for the same package. The discrepancy meant insufficient postage and a returned package.
- **Thread:** https://community.shopify.com/c/payments-shipping-and/discrepancy-from-usps-to-shopify-shipping-rates/td-p/2045103

---

## Shipping Profiles & Configuration

**9. Double shipping charges from multiple profiles**
- **User:** Cowfee_Art
- **Date:** March 13, 2021
- **Quote:** "I can't believe this isn't a shopify feature. It's super annoying, bad UX"
- **Issue:** When products from different shipping profiles are in the same cart, Shopify adds both rates ($5 + $5 = $10) instead of charging a single fee or the highest rate. No native solution exists.
- **Thread:** https://community.shopify.com/t/stop-merging-different-shipping-profiles/39368

**10. 100 shipping profile limit blocks POD stores**
- **User:** outlier
- **Date:** December 9, 2023
- **Quote:** "Shopify limits us to 99 custom shipping profiles (100 total including general profile). A store with 100+ total product-variant combinations from Printify can't exist on Shopify."
- **Quote:** "The fact that we are both small stores and easily go over this limit underscores what an obvious oversight it is."
- **Issue:** Print-on-demand merchants cannot create accurate per-variant shipping profiles. Etsy handles this seamlessly.
- **Thread:** https://community.shopify.com/c/payments-shipping-and/shipping-profile-limit-and-printify-pod-how-can-i-make-this-work/td-p/2351452

**11. Forced to embed shipping in product price**
- **User:** vanessuca
- **Date:** February 23, 2024
- **Quote:** "the only solution is to offer free shipping on certain products and embed the shipping price in the product price"
- **Issue:** Due to shipping profile limits, merchant has no way to set accurate per-product shipping and must hide shipping costs in product prices as a workaround.
- **Thread:** https://community.shopify.com/c/payments-shipping-and/shipping-profile-limit-and-printify-pod-how-can-i-make-this-work/td-p/2351452

**12. Bulk product assignment to profiles impossible**
- **User:** 3Adigit
- **Date:** September 8, 2023
- **Quote:** "Do I have to manually assign products to the profiles? I have 1000s of products..."
- **Issue:** No native CSV or bulk assignment for shipping profiles. Must use a third-party app. Rates from multiple profiles can only be added, never showing just the highest rate.
- **Thread:** https://community.shopify.com/c/shopify-discussions/shipping-profiles-problems-painful-to-add-products-to-profiles/m-p/2217268

---

## Plan Gating & Cost Barriers

**13. Real-time carrier rates locked behind $399/month plan**
- **User:** Sheryl89
- **Date:** June 13, 2025
- **Quote:** "I need better shipping options to potentially grow my sales, but Shopify wants me to pay $399/month when I'm making minimal revenue."
- **Issue:** Calculated carrier rates only available on Advanced plan. Store has 0.9% conversion rate and 80% bounce rate, partly attributed to shipping limitations.
- **Thread:** https://community.shopify.com/t/shipping-pricing-creates-barrier-for-small-businesses/419020

**14. 5+ years and still cannot figure out carrier-calculated shipping**
- **User:** ReneeM
- **Date:** August 4, 2025
- **Quote:** "I have both USPS and UPS accounts... I have not been able to figure this out in the 5 plus years I have been here."
- **Issue:** Despite having her own carrier accounts, merchant cannot configure real-time calculated shipping properly on Shopify's Grow plan.
- **Thread:** https://community.shopify.com/t/shipping-pricing-creates-barrier-for-small-businesses/419020

---

## Local Pickup & Delivery

**15. Local pickup blocked when cart has items from multiple locations**
- **User:** gayled
- **Date:** June 1, 2024
- **Quote:** "if they choose stock from different location we get an error" — the error being "Pickup isn't available for this order. Choose another delivery method."
- **Issue:** Shopify cannot offer local pickup when products in the cart originate from two or more warehouse locations. Confirmed by Shopify staff as a known limitation with no native fix.
- **Thread:** https://community.shopify.com/t/pickup-isnt-available-for-this-order-choose-another-delivery-method-error-on-local-pickup/327974

**16. Multi-location checkout silently breaks**
- **User:** pythagoryan
- **Date:** December 5, 2023
- **Quote:** "the checkout page will bug out and never fully load. There's not even an error message."
- **Quote:** "There's no built-in or third party method that I can find which will allow users to select a location"
- **Issue:** When items are not available at a single location, checkout fails silently. No built-in method for customers to select a preferred pickup location. Had to pay for Zapiet's premium plan to fix it.
- **Thread:** https://community.shopify.com/t/multi-location-local-pickup-and-delivery-only-store-issues/274817

**17. Multi-vendor local delivery completely blocked**
- **User:** plantbaby
- **Date:** December 15, 2022 (still unresolved March 2025)
- **Quote:** "User goes to checkout with 1 plant from one vendor/location, and 1 plant from another vendor location. User tries to checkout and selects local pickup. Shopify throws an error message."
- **Issue:** Both pickup AND delivery fail when cart contains items from multiple vendor locations. Problem reported December 2022, another merchant asked in March 2025: "Did you find a solution that works for you now?" — still no resolution.
- **Thread:** https://community.shopify.com/t/how-to-resolve-local-delivery-and-pickup-issues-for-multiple-locations-on-a-plant-store/176639

---

## Refunds & Support

**18. $1,300 in unrefundable voided USPS labels**
- **User:** jacktheripper
- **Date:** October 2023
- **Quote:** "The Shopify website displayed a troubling 'System error' message before all 10 void buttons became unresponsive."
- **Quote:** "For a small business like ours, this sum is tantamount to depriving our hardworking employees of their deserved salaries."
- **Issue:** 10 of 13 USPS labels could not be voided due to system errors. Both Shopify and USPS redirect blame to each other, leaving merchant stuck with $1,300 in charges.
- **Thread:** https://community.shopify.com/c/payments-shipping-and/shopify-shipping-refund-nightmare-with-usps-please-help/m-p/2285920

---

## Checkout Display Issues

**19. Updated shipping rates not showing at checkout**
- **User:** bristol500
- **Date:** February 17, 2024
- **Quote:** "all of my carts at checkout continue to show my old shipping price"
- **Issue:** After switching from free shipping to conditional free shipping with a minimum order, old rates persist at checkout despite deleting and recreating the shipping profile.
- **Thread:** https://community.shopify.com/c/shopify-discussions/why-won-t-my-updated-shipping-rates-show-at-checkout/m-p/2448923

**20. "Cannot be shipped" error on valid addresses**
- **User:** sundayflea
- **Date:** January 19, 2024
- **Quote:** "Your order cannot be shipped to the selected address. Review your address..."
- **Issue:** Multiple customers unable to complete orders despite verified addresses (e.g., ZIP 10012 in New York). Root cause was hidden misconfiguration across multiple shipping profiles — one profile had zero rates configured, blocking all orders.
- **Thread:** https://community.shopify.com/t/customer-order-error-your-order-cannot-be-shipped-to-the-selected-address/287083

---

## Key Patterns

### 1. Rate accuracy is fundamentally broken
Shopify does not handle dimensional weight, multi-package shipments, or carrier rate synchronization correctly. Merchants either lose money (undercharged customers, label costs exceed checkout price) or lose customers (overcharged at checkout, cart abandonment). This is not an edge case — it affects anyone selling heavy, bulky, or multi-item orders.

### 2. Shipping profiles are rigid and do not scale
The 100 profile limit, lack of bulk assignment, and additive-only rate logic across profiles make shipping configuration painful for any store with product variety. POD stores are especially blocked. There is no "use highest rate" or "use lowest rate" option — only addition.

### 3. Multi-location is an afterthought
Local pickup and delivery fail completely when a cart contains items from more than one location. Checkout either errors out or silently breaks. This has been a known limitation for years (2022-2025) with no native fix, only third-party paid apps.

### 4. Core shipping features are gated behind expensive plans
Real-time carrier-calculated rates require the $399/month Advanced plan. Small merchants are stuck with flat rates or Shopify's own discounted rates, which often do not match actual carrier costs. This creates a catch-22: you need sales to afford better shipping, but bad shipping kills sales.

### 5. Support is absent when shipping goes wrong
Multiple merchants report being unable to reach anyone when shipping billing disputes arise. Shopify and carriers blame each other. Voided labels do not get refunded. Rate discrepancies go unresolved for months. For a platform that processes billions in GMV, the shipping support infrastructure does not match.

### 6. Configuration complexity causes silent failures
Shipping zones, profiles, and carrier settings interact in ways that are hard to debug. A single misconfigured profile can block checkout for all customers. Updated rates do not always propagate. There is no validation or warning system to catch these issues before they cost sales.
