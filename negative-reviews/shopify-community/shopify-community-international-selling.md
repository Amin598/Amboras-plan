# Shopify Community: International Selling, Multi-Currency, Multi-Language & Markets Complaints

Source: community.shopify.com (Shopify's official merchant forums)
Collected: March 2026

---

## 1. Shopify Markets Forced on Merchants

**User:** Birgita | **Date:** August 29, 2024
**Thread:** [International Selling when you don't want to use markets](https://community.shopify.com/t/international-selling-when-you-dont-want-to-use-markets/353424/1)

> "I don't want to use markets. Is this not an option to ship international without any of the silly market stuff?"

> "It seems to just want to get all sorts of extra fees."

> "Now Shopify starts with markets and all my international shipping profiles are 'inactive'"

**Issue:** Shopify Markets appears mandatory for international shipping. Existing custom shipping profiles were deactivated when Markets was introduced, forcing merchants into a system they didn't choose. Even simplified configurations incur a 2% currency conversion fee.

---

## 2. Shopify Markets Produces "Commercially Broken" Pricing

**User:** UBW | **Date:** February 6, 2026
**Thread:** [Why is Shopify Markets killing my conversion rates with bad math?](https://community.shopify.com/t/why-is-shopify-markets-killing-my-conversion-rates-with-bad-math/587500)

> "No retailer in Denmark wants to sell a premium product for '701.00 DKK'. It looks unprofessional."

> "A flat +x% doesn't fix the rounding; it just moves the 'ugly' number to a different ugly number."

> "Impossible to maintain with a catalog of hundreds/thousands of SKUs."

> "Fixed prices in secondary currencies creates 'reverse conversion' nightmares for those running POS/physical stores."

> "Shopify is forcing us to choose between unprofessional pricing or hundreds of hours of manual labor."

**Issue:** Currency conversion produces ugly, unrounded prices that look unprofessional. No psychological pricing rules (e.g., round to .95 or .99). Manual overrides are impractical at scale. Fixed prices create reverse-conversion problems for POS.

---

## 3. Discount Codes Break Across Markets

**User:** BlueOceangrowth | **Date:** July 22, 2024
**Thread:** [Amount off $$ Discount codes issues with different markets](https://community.shopify.com/t/amount-off-discount-codes-issues-with-different-markets/341619)

> "When I create a discount code for a fixed amount off (e.g., $10 off $50), it works fine in Canada...However, for the US market, it converts to approximately $7, which is misleading"

**Issue:** Fixed-amount discount codes are auto-converted between currencies, producing confusing and misleading values for customers in non-default markets.

---

## 4. Checkout Empties Cart When Market Unavailable

**User:** beebebs | **Date:** November 22, 2023
**Thread:** [Markets - products not available at checkout, empties your basket](https://community.shopify.com/c/shopify-discussions/markets-products-not-available-at-checkout-empties-your-basket/td-p/2326479)

> "all 3 markets are displayed on the country option"

> "Empties the user's basket" and "Diverts you back to the homepage"

> "there is no 'Go Back' the ONLY option is to 'Return to store'"

> "no users are going to start their shopping journey again...it will likely end up in people dropping off"

**Issue:** Selecting an unavailable market at checkout clears the entire cart and redirects to the homepage with no way to recover. Massive conversion killer.

---

## 5. Multi-Currency Checkout Doesn't Actually Work

**User:** CK3 | **Date:** July 18, 2021
**Thread:** [Multi-currency checkout & free shipping conditions](https://community.shopify.com/t/multi-currency-checkout-free-shipping-conditions/53732/1)

> "When I try to checkout, the default checkout currency is still in SGD. What should I do to change the checkout currency to the home currency of the customer?"

> "Once my customers start checking out in different currencies, how do I extend the same offer to international customers in their home currency?"

**Issue:** Despite enabling multi-currency, checkout stays in the store's default currency. Free shipping thresholds don't convert across currencies -- a SGD 150 threshold doesn't adapt for international customers.

---

## 6. Currency Selector Doesn't Switch Currencies

**User:** BmaxStore | **Date:** March 2, 2022
**Thread:** [Why isn't my multi-currency store switching currencies?](https://community.shopify.com/t/why-isnt-my-multi-currency-store-switching-currencies/103571)

> "Current currency is Euro, but if I select USA the currency remains Euro"

> "the Manage at Currency and pricing is disabled and I can't enable it"

**Issue:** Currency selector UI is present but non-functional. Settings to manage currency pricing are disabled with no clear way to enable them.

---

## 7. API Returns Wrong Currency for Markets

**User:** je2e495DEV | **Date:** March 17, 2022
**Thread:** [Facing issues with multi-currency product pricing in markets](https://community.shopify.com/t/facing-issues-with-multi-currency-product-pricing-in-markets-is-it-a-bug/107355)

> "it returns the USD (store currency) price instead of the converted price"

> "changes the cart_currency cookie value from, ie.: USD to ARS and again to USD"

**Issue:** The /products.json endpoint returns base currency instead of the market-converted price. Currency cookies fluctuate unexpectedly, breaking the experience for developers building on top of Markets.

---

## 8. Managed Markets Holds Thousands in Payouts

**User:** tordizzy | **Date:** September 14, 2024
**Thread:** [Issues with Payouts for Managed Markets](https://community.shopify.com/c/managed-markets/issues-with-payouts-for-managed-markets/m-p/2653450)

> "I have thousands of dollars being held by Shopify even though all the orders have been picked up by DHL."

**User:** JNS594 | **Date:** July 9, 2024

> "I currently have 22 orders with Blocked payments. Most of them have already passed through the DHL facility in Erlanger KY."

**User:** snowcountry | **Date:** October 16, 2024

> "DHL E Commerce, never got out of the US. (where did those packages go???)"

> "We will NEVER use DHL E Commerce for international shipments, again!"

**Issue:** Managed Markets holds merchant payouts for extended periods, even after packages are confirmed picked up by carriers. Some DHL eCommerce shipments never leave the US, and merchants have no recourse. Thousands of dollars stuck.

---

## 9. Translation Limited to 2 Auto-Translate Languages

**User:** Tiparts | **Date:** October 16, 2023
**Thread:** [More than 2 auto-translation languages in Shopify Translate and Adapt](https://community.shopify.com/t/more-than-2-auto-translation-languages-in-shopify-translate-and-adapt/151872)

> "Hi Admin, after a year, this app still limit to 2 languages. We need more please."

**User:** rv3 | **Date:** November 2, 2023

> "the maximum 2 is a bit frustrating to shops from the EU"

**User:** DonnaC | **Date:** April 10, 2024

> "the manual method is hideously cruel" (with "thousands of blog articles" across ten languages)

**User:** MVWebmaster | **Date:** August 28, 2023

> "+1 here. Having ability to translate into more than 2 languages (either free or for a fee) would be nice to have."

**Issue:** Shopify's Translate & Adapt app only auto-translates 2 languages. EU merchants selling across multiple countries are forced to manually translate thousands of pages. The manual method is described as "hideously cruel."

---

## 10. Translations Get Lost or Break After Changes

**User:** raffaelebatori | **Date:** July 2023
**Thread:** [Problem with Translations using Translate & Adapt](https://community.shopify.com/t/problem-with-translations-using-translate-adapt/232419)

> "it translates only one language. It tells me that the automatic translation limit has been exceeded."

> "I also wanted to translate the URLs into English and French" (not supported)

> "the column labeled 'translated content' within the CSV files attached in these emails is empty."

**User:** Dunacase | **Date:** November 20, 2023

> (Reports that changing default language to Hungarian caused loss of all manual Hungarian edits, contradicting support's assurance that "manually edited" translations would be preserved)

**Issue:** Translations disappear after reinstallation. URL/handle translation not supported. Changing default language wipes out manual translations despite being told otherwise by support.

---

## 11. Cart Page Reverts to Default Language

**User:** nathanot19 | **Date:** October 4, 2022
**Thread:** [How to fix cart page language switch issue in a multi language store?](https://community.shopify.com/t/how-to-fix-cart-page-language-switch-issue-in-a-multi-language-store/157033)

> "When you go to the shopping cart it automatically switches the languages back to the primary language"

Related reports from the same thread:
- "Products on checkout disappears when changing the language on any of cart pages" (September 25, 2023)
- "Checkout Language is always in English, how to fix that?" (December 2, 2024)
- "Cart and checkout pages don't work in different language" (June 30, 2024)

**Issue:** Widespread problem where cart and checkout revert to the store's default language regardless of customer selection. Products can even disappear from checkout when switching languages.

---

## 12. International Pricing Has No Rounding Rules

**User:** ajmarriage | **Date:** May 18, 2021
**Thread:** [Setting international price rules and rounding up](https://community.shopify.com/t/selling-internationally-setting-international-price-rules-and-rounding-up/46875)

> "Cannot seem to find rules for rounding up or down on 5 or 10 increments e.g. if price is converted to $43 we would rather show it as $45"

> "if the user clicks x (which we are finding is common due to user disdain for popups) then the pricing remains unchanged"

**User:** LibertineFragra | **Date:** June 4, 2021

> "allowing the prices in different regions to be very available is a great way to cause frustrations in customers that are paying the higher price"

**Issue:** No rounding rules for converted prices. Geolocation popup dismissed = prices don't change. Transparent regional pricing differences frustrate customers paying the higher price.

---

## 13. Cannot Set Different Default Languages Per Market

**User:** Ingrid1234 | **Date:** March 19, 2024
**Thread:** [Best practice for selling in multiple markets and languages](https://community.shopify.com/c/international-commerce/best-practice-for-selling-in-multiple-markets-and-languages/m-p/2494238)

> "the default language in Norway would be Norwegian, but for the International market, it would be English. But this is not possible"

> "I struggle with translating the content on our website, as this has to be done in the editing tool, and not in the Translate app"

> "Coming from Wix, the setup in Shopify was a bit confusing at first to be honest, even for me with a technical background"

**Issue:** Shopify forces one global default language. Cannot set Norwegian for Norway and English for international. Translation workflow split between editing tool and Translate app is confusing. Even technically-skilled users find it harder than Wix.

---

## 14. SEO Tanks After Enabling Markets with Multi-Domains

**User:** Hansdieter | **Date:** July 15, 2022
**Thread:** [SEO issues Shopify Markets with multi domains](https://community.shopify.com/t/seo-issues-shopify-markets-with-multi-domains/135514)

> "We are experiencing duplicate content problems now. We see that german keywords get indexed for the french domain"

**User:** Niko8 | **Date:** May 23, 2024

> "After launch we have notice a drop on SEO performance, due to, duplicate content, not indexed"

**Issue:** Multi-domain Markets setup creates duplicate content problems. Wrong language pages get indexed for wrong country domains. Direct SEO performance drops observed.

---

## 15. International Orders Stuck on Single Market/Currency

**User:** (from thread) | **Date:** 2025
**Thread:** [Facing Issues with Creating International Orders and Invoices](https://community.shopify.com/t/facing-issues-with-creating-international-orders-and-invoices-only-india-market-and-inr-showing/568643)

Issue described: Merchant can only create orders in India Market with INR, despite wanting to sell internationally. Other markets and currencies don't appear as options.

**Issue:** International selling locked to a single market. Unable to create orders or invoices in other currencies despite having Markets configured.

---

## Key Patterns for Amboras

| Pattern | Frequency | Amboras Opportunity |
|---|---|---|
| Currency conversion produces ugly/unprofessional prices | High | AI-powered psychological pricing rules per market |
| Translation limited to 2 languages, manual is brutal | High | AI auto-translation for unlimited languages, built-in |
| Cart/checkout breaks when switching language or market | High | Seamless multi-language/multi-currency from day one |
| Markets forced on merchants who want simple international | High | Simple international shipping without complex market setup |
| Discount codes don't convert properly across markets | Medium | Market-aware promotions that auto-adapt |
| Managed Markets holds payouts for weeks | Medium | Transparent international payment processing |
| SEO breaks with multi-domain/multi-language | Medium | Proper hreflang and indexing built into the platform |
| No per-market default language | Medium | Market-specific language defaults |
| Geolocation popup required for currency switching | Medium | Automatic, seamless currency detection |
| Fixed prices create reverse-conversion nightmares | Medium | Intelligent pricing engine that handles both directions |
