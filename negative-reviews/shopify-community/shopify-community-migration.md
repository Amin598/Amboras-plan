# Shopify Community Forum — Migration Issues & Data Portability

Source: community.shopify.com (official Shopify forums)
Collected: March 2026

These are real complaints from merchants on Shopify's own community forum about migration pain — both migrating TO and FROM Shopify, as well as data export/import limitations. Quotes are taken directly from users.

---

## Complaints

**1. Duplicated orders, corrupted stats, no way to reset store data**
- User: MarcinK71
- Date: November 9, 2023
- Quote: "I have all orders duplicated, but with different numbers... All statistics is still wrong, not removed... I need PLEASE option to reset my shop data. This is very urgent."
- Quote: "There is no way to wipe out the store data, for example unfulfilled orders will stay forever."
- Quote: "I had to do migration 5-7 times and now I have all this wrong."
- Issue: After multiple migration attempts, store data was corrupted with duplicate orders and wrong statistics. No built-in way to reset or clean up.
- Thread: https://community.shopify.com/c/shopify-discussions/problems-after-migration-with-duplicated-orders-and-data/m-p/2305107

**2. Week-long migration spinning wheel with zero feedback**
- User: CaptainTs
- Date: June 20, 2025
- Quote: "Watched a spinning wheel and its 'Migration in Progress' message for nearly a week now."
- Quote: "No error messages, no error codes. Just the wheel. THE WHEEL!"
- Issue: Migration tool provided no progress indicator, no error handling, no feedback. With 28,000+ inventory items, manual re-entry was described as "a Worst Case scenario situation."
- Thread: https://community.shopify.com/t/qb-pos-ver-19-to-shopify-migration-nightmare/420360

**3. Product images and variations vanished, kept charging fees**
- User: ArtOlo
- Date: October 12, 2024
- Quote: "My store was hit with technical issues that caused product images and variations to disappear."
- Quote: "Shopify continued to charge me monthly fees even though my store was unusable."
- Quote: "They continued charging me their monthly membership fee the entire time."
- Issue: Technical issues during migration caused data loss. Shopify continued billing despite the store being non-functional. No compensation offered.
- Thread: https://community.shopify.com/c/technical-q-a/shopify-technical-issues-data-loss-and-no-compensation-months-of/td-p/2805892

**4. No automatic backups, no SLA, no guarantees**
- User: PaulNewton
- Date: October 12, 2024
- Quote: "Shopify may 'claim' 99.9% uptime but that is not a guarantee."
- Issue: Platform provides no automatic backup system, no log system, and no Service Level Agreement. Merchants are fully responsible for their own data integrity.
- Thread: https://community.shopify.com/c/technical-q-a/shopify-technical-issues-data-loss-and-no-compensation-months-of/td-p/2805892

**5. Total SEO collapse after migration to Shopify**
- User: HDAD
- Date: January 27, 2026
- Quote: "We have seen a huge loss in SEO traffic... simply do not appear in results anymore vs being visible on page 1 or 2."
- Quote: "Is our SEO rank lost, even if we told Google that domain X became the new domain Y?"
- Issue: Complete loss of search engine visibility after migrating to Shopify with a new domain. Slow 6-7 month migration process with incomplete 301 redirects compounded the damage.
- Thread: https://community.shopify.com/t/lost-seo-after-migration-to-shopify-and-new-domain/586117

**6. Blog URL structure forced change destroys SEO**
- User: alex-stoykov
- Date: March 28, 2024
- Quote: "Our SEO ranking is heavily affected by our blog posts and that is where we get the most ranks from."
- Issue: WordPress uses `website.com/blog-post-name` while Shopify forces `website.com/blogs/news/blog-post-name`. No way to preserve old URL structure. Redirects help but don't fully preserve SEO value.
- Thread: https://community.shopify.com/t/how-to-migrate-blog-posts-to-shopify-without-losing-seo-ranking/309217

**7. Multiple platform migrations compound SEO damage**
- User: BBBGEM
- Date: February 19, 2025
- Quote: "We migrated our website from BigCommerce to WordPress, and then from WordPress to Shopify. Due to multiple migrations, it has resulted in a loss of SEO ranking."
- Issue: Each migration creates redirect chains that dilute SEO authority. Shopify's rigid URL structure makes it impossible to maintain continuity.
- Thread: https://community.shopify.com/t/how-to-quickly-recover-the-lost-ranking-after-migrating-to-shopify/395619

**8. Collections cannot be exported — just gone**
- User: benwrigley
- Date: January 15, 2024
- Quote: "When I import them into the demo, all the collections have gone."
- Issue: Shopify admin does not support exporting collections or pages. Community confirmed: "The Shopify admin panel does not support it." Moving between Shopify stores means recreating collections manually.
- Thread: https://community.shopify.com/t/export-data-to-new-shop-doesnt-bring-collections/285286

**9. CSV export emails never arrive — broken for years**
- User: Blaft (September 2021)
- Quote: "Impossible to export a bigger batch — an email is promised but never arrives."
- User: user1232 (November 2021)
- Quote: "Only way I can get file exports is if customer service emails them."
- User: Delaia24 (December 2021)
- Quote: "Problem is marked as solved however this issue still seems to exist."
- User: WildFlowersofNY (January 2023)
- Quote: "Why are you not fixing this? It is 2023 and you still have this issue."
- Issue: CSV export functionality broken for multiple users across years. Exports promised via email never arrive. Issue repeatedly marked as "solved" despite persisting.
- Thread: https://community.shopify.com/c/shopify-discussions/shopify-export-to-csv-issue-file-is-never-sent/td-p/1160012

**10. Can't export orders or customers at all**
- User: Mediocre
- Date: April 22, 2022
- Quote: "When I try to export my Orders or Users, they do not get sent to my email address. I have tried different types of exports, from all Orders to just the Current Page to a Date Range."
- Issue: Export functionality completely non-functional. No alternative download method available in the admin.
- Thread: https://community.shopify.com/c/shopify-discussions/can-t-export-customers-or-orders/td-p/1567548

**11. Metafield export partially broken, undocumented limitations**
- User: jamesanderson
- Date: October 4, 2024
- Quote: "I can get access to Boolean type metafields — but no 'List of values' type metafields."
- Quote: "They partly enable features but provide no documentation that helps you decide if you want to use that functionality because of limitations."
- Issue: Metafield export works for some types but silently fails for others. No documentation on what is and isn't exportable.
- Thread: https://community.shopify.com/t/how-to-bulk-export-and-bulk-import-all-the-metafields-in-products/63742/26

**12. Metafield definitions can't transfer between stores**
- User: Tristan3dt
- Date: January 17, 2023
- Quote: "It would save a lot of tedious and error-prone copy and pasting when it comes to deploy the theme onto our live site."
- Issue: ~20 metafield definitions had to be recreated manually when moving between dev and production stores. API documentation unclear on how to automate this.
- Thread: https://community.shopify.com/t/import-export-metafield-definitions-between-stores-or-by-api/184409

**13. Leaving Shopify means rebuilding from scratch**
- User: StephensWorld (responding to RJ202020)
- Date: March 3, 2024
- Quote: "You'd essentially have to rebuild the site from scratch... there's no way to just bulk move everything off of Shopify and have it look/work the exact same."
- Issue: No comprehensive export. Theme code, collections, pages, metafields, customizations — none of it transfers. Vendor lock-in is total.
- Thread: https://community.shopify.com/c/shopify-discussions/how-to-migrate-a-store-from-shopify-to-justhost/m-p/2471086

**14. "Huge mistake choosing Shopify"**
- User: bryan76
- Date: June 3, 2024
- Quote: "I would most certainly leave Shopify before moving to Shopify Plus. Not a consideration for us."
- Quote: "Many have said I made a huge mistake choosing Shopify and I am now realizing why."
- Issue: Frustration with platform limitations compounded by the realization that leaving means losing everything you built.
- Thread: https://community.shopify.com/t/guest-checkout-options/328281/7

**15. Statement of charges export limited to 90 days — no warning**
- User: blconn (November 30, 2019)
- Quote: "We're now missing a critical piece of our business data."
- Quote: "Shopify would disable a function like this with no notice and no possible recourse."
- User: James22222 (June 10, 2020)
- Quote: "This is absolutely absurd. How do you continue removing useful features."
- User: snehal (July 7, 2020)
- Quote: "It's ANTI-transparent and gives the impression that the company is trying to hide charges."
- User: George_C (July 9, 2020)
- Quote: "I can't even comprehend how anyone on the development team could justify removing access."
- User: David238 (October 9, 2020)
- Quote: Called it "really terrible business practice" never encountered elsewhere for financial records.
- Issue: Shopify silently reduced billing data export from full history to 90 days. Merchants lost access to their own financial records with no warning.
- Thread: https://community.shopify.com/c/accounting-and-taxes/statement-of-charges-only-available-for-90-days-need-export-for/td-p/614193

**16. Merchant forced to write code to scrape their own billing data**
- User: blconn
- Date: December 7, 2019
- Quote: Described resorting to writing custom jQuery code to manually scrape billing data from Shopify's admin interface.
- Issue: After the 90-day export limitation was imposed, a merchant had to reverse-engineer their own billing history from the platform. This is their own data.
- Thread: https://community.shopify.com/c/accounting-and-taxes/statement-of-charges-only-available-for-90-days-need-export-for/td-p/614193

**17. Data inconsistency after database migration — zero help**
- User: Jessica_Shawn
- Date: December 13, 2023
- Quote: "Certain tables failed to transfer accurately, leading to data inconsistencies."
- Issue: Database migration produced inconsistent data across tables. Thread received zero responses or solutions from Shopify or community.
- Thread: https://community.shopify.com/t/data-inconsistency-in-recent-database-migration/277165

**18. Developers accidentally set noindex during migration**
- User: rahul_ghoghari
- Date: May 21, 2025
- Quote: "I've seen my developer deliver store after migration that has set noindex, nofollow tag."
- Issue: Migration process so complex that critical technical errors (like blocking search engines entirely) go unnoticed. No built-in migration checklist or safeguards.
- Thread: https://community.shopify.com/t/how-to-quickly-recover-the-lost-ranking-after-migrating-to-shopify/395619

**19. CSV import deletes existing images — known destructive behavior**
- Issue: Importing a CSV file can break image associations and delete existing images. Sorting columns/rows fragments products because the CSV importer processes row-by-row. Including only the first variant risks losing all other variants and their associated images.
- Multiple users affected across several years (2020-2025). Known issue, no fix.
- Threads:
  - https://community.shopify.com/c/technical-q-a/shopify-csv-import-deleting-images-here-s-my-solution/td-p/1325527
  - https://community.shopify.com/t/lost-variations-and-images/333951/7
  - https://community.shopify.com/t/urgent-missing-product-images-after-import-possible-rollback/396027

**20. Customers can't export their own order history**
- User: NoelHayden
- Date: July 25, 2023
- Quote: "I am looking for a way for a customer to export their own order history."
- Issue: Shopify has no native functionality for customer-facing order data export. Only merchant-side export exists, and even that is unreliable (see complaints 9-10).
- Thread: https://community.shopify.com/t/can-customers-export-their-own-order-history-into-a-csv-spreadsheet/235588/3

---

## Key Patterns

### 1. Vendor Lock-In Is Total
Shopify makes it nearly impossible to leave cleanly. There is no full export of collections, pages, metafields, or theme customizations. Community members openly confirm: "You'd essentially have to rebuild from scratch." This is not a bug — it is a business model.

### 2. Migration TO Shopify Is Also Painful
Moving to Shopify destroys SEO due to forced URL structures (`/blogs/news/` prefix, `/products/` prefix). CSV imports delete images, duplicate orders, and fragment product variants. Migration tools provide no progress feedback and fail silently.

### 3. Export Is Deliberately Limited
Billing data capped at 90 days with no warning. CSV exports that never arrive via email. Metafield types that silently fail to export. Collections that simply don't export at all. The pattern is consistent: Shopify restricts access to your own data.

### 4. No Backups, No SLA, No Safety Net
Merchants are fully responsible for their own data integrity on a platform that provides no automatic backups, no log system, and no Service Level Agreement. When data loss occurs, Shopify continues billing and offers no compensation.

### 5. The CSV Paradigm Is Broken
Shopify's reliance on CSV for data portability is fundamentally fragile. It destroys images when rows are reordered, fragments product variants, fails silently at scale, and the email delivery mechanism for large exports has been broken for years.

### 6. Your Financial Records Are Not Yours
Shopify silently reduced billing export from full history to 90 days. Merchants lost access to their own financial data with no warning. One merchant resorted to writing jQuery scraping code to extract their own billing history.

---

## Amboras Opportunity

Every one of these complaints maps directly to the Amboras thesis:

- **Full data portability from day one**: Open export of everything — products, collections, pages, orders, customers, metafields, themes, financial records. No exceptions, no limitations, no silent failures.
- **Migration that doesn't destroy SEO**: Flexible URL structures that can match any source platform. No forced prefixes.
- **Automatic backups with SLA**: Real guarantees, not marketing claims.
- **No CSV dependency**: Modern API-first import/export that handles images, variants, and relationships as first-class objects.
- **Your data is your data**: Full history, always available, always exportable. No 90-day caps. No "email that never arrives."
