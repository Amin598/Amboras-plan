# Shopify Community Forum Reviews — Liquid Templating & Developer Experience

Collected from community.shopify.com. Sourced March 2026.

---

## Liquid Language Limitations

---

**1.** "Liquid your custom html template language...doesn't really support basic programming features like removing an element from an array or collection"

**Source:** [Shopify Community — Hide out of stock items](https://community.shopify.com/t/your-developers-need-to-make-it-easier-to-hide-out-of-stock-items-how-to-edit-my-liquid-template/302009)
**User:** hudlee
**Date:** March 4, 2024

**Key issue:** Liquid lacks basic programming capabilities; cannot manipulate arrays or collections

---

**2.** "THERE APPEARS TO BE NO WAY TO CREATE OBJECTS IN LIQUID"

**Source:** [Shopify Community — Hide out of stock items](https://community.shopify.com/t/your-developers-need-to-make-it-easier-to-hide-out-of-stock-items-how-to-edit-my-liquid-template/302009)
**User:** hudlee
**Date:** March 4, 2024

**Key issue:** Cannot create custom key/value objects in Liquid; a fundamental programming capability is missing entirely

---

**3.** Array 'inStockProducts' is not paginateable — the paginate tag "can only accept specific Shopify-provided arrays"

**Source:** [Shopify Community — Hide out of stock items](https://community.shopify.com/t/your-developers-need-to-make-it-easier-to-hide-out-of-stock-items-how-to-edit-my-liquid-template/302009)
**User:** hudlee
**Date:** March 4, 2024

**Key issue:** Liquid pagination only works on Shopify's built-in arrays, not custom-filtered ones; severely limits what developers can build

---

**4.** "Why isn't there a liquid method for me to construct my own key/value objects and arrays?"

**Source:** [Shopify Community — Insanely slow theme development](https://community.shopify.com/t/simple-changes-to-improve-insanely-slow-theme-development-on-shopify/23905)
**User:** jeremygottfried
**Date:** October 29, 2020

**Key issue:** Liquid lacks fundamental data structure creation capabilities that any modern language provides

---

**5.** "the forloop in Liquid is limiting me to 50 at a time" when trying to display 366 products

**Source:** [Shopify Community — Trouble using Liquid to display 366 items](https://community.shopify.com/t/trouble-using-liquid-to-display-366-items/572121)
**User:** noahADD
**Date:** October 23, 2025

Community member AndyX confirmed: "Liquid loops in storefront themes are capped at 50 iterations for performance reasons, so there isn't a way to simply loop over all 366 products in a single page."

**Key issue:** Liquid for-loops are hard-capped at 50 iterations; cannot display large datasets without pagination hacks

---

**6.** "Actually there's NO WAY to share section content across multiple templates."

**Source:** [Shopify Community — Online Store 2.0 reuse of section content](https://community.shopify.com/c/shopify-design/online-store-2-0-reuse-of-section-content-like-it-was-before/m-p/1287875)
**User:** albertoziveri
**Date:** October 11, 2021

**Key issue:** Online Store 2.0 broke section content reuse; developers must now replicate content in every JSON template

---

**7.** The Liquid `render` operator "doesn't support json templates," blocking workarounds for shared content

**Source:** [Shopify Community — Online Store 2.0 reuse of section content](https://community.shopify.com/c/shopify-design/online-store-2-0-reuse-of-section-content-like-it-was-before/m-p/1287875)
**User:** albertoziveri
**Date:** August 24, 2021

**Key issue:** Fundamental architectural limitation in OS 2.0 with no workaround for content reuse across templates

---

## Development Workflow & Tooling

---

**8.** "Shopify has an insanely slow theme development cycle."

**Source:** [Shopify Community — Insanely slow theme development](https://community.shopify.com/t/simple-changes-to-improve-insanely-slow-theme-development-on-shopify/23905)
**User:** jeremygottfried
**Date:** October 29, 2020

**Key issue:** No localhost server, no real-time code updates, must deploy every minor change to see results

---

**9.** "Shopify has no Local Development solution whatsoever" ... "I would not advise any clients that require heavy customization to move to Shopify"

**Source:** [Shopify Community — Insanely slow theme development](https://community.shopify.com/t/simple-changes-to-improve-insanely-slow-theme-development-on-shopify/23905)
**User:** MikeMK
**Date:** December 19, 2020

**Key issue:** No local dev environment, no built-in Webpack/NPM support, Slate was deprecated with no replacement

---

**10.** "Having to build sites on something like Dreamweaver in 2023 is shocking"

**Source:** [Shopify Community — Website builder is garbage](https://community.shopify.com/t/shopifys-website-builder-is-garbage-and-our-business-is-suffering-almost-wish-i-never-switched/161168)
**User:** KellyBrito (professional designer/developer)
**Date:** November 16, 2023

**Key issue:** Even experienced developers find Shopify's development workflow archaic and outdated

---

## Theme Editor Regressions

---

**11.** "new theme editor that is much slower and harder to read than the original"

**Source:** [Shopify Community — How to disable the new theme editor](https://community.shopify.com/t/how-to-disable-the-new-theme-editor/552482)
**User:** ScalaApps
**Date:** July 31, 2025

**Key issue:** New code editor is a performance regression; slower and worse readability than the classic editor

---

**12.** Takes "minutes for a fullblown IDE to bootup" for simple edits — criticizes forcing "a full blown developers IDE onto merchants"

**Source:** [Shopify Community — How to disable the new theme editor](https://community.shopify.com/t/how-to-disable-the-new-theme-editor/552482)
**User:** PaulNewton
**Date:** July 31, 2025

**Key issue:** Shopify replaced a simple editor with an over-engineered IDE that is slow to load and inappropriate for non-developers

---

**13.** "old editor was easy for my clients to use" but the new one makes it "more difficult for them"

**Source:** [Shopify Community — How to disable the new theme editor](https://community.shopify.com/t/how-to-disable-the-new-theme-editor/552482)
**User:** Ketan_Mistry
**Date:** August 4, 2025

**Key issue:** Clients (non-developers) can no longer make simple code edits; the new editor is intimidating

---

**14.** Describes the new theme editor tool as "terrible and clumsy"

**Source:** [Shopify Community — How to disable the new theme editor](https://community.shopify.com/t/how-to-disable-the-new-theme-editor/552482)
**User:** zoicpete
**Date:** September 12, 2025

**Key issue:** Overall poor UX of the new code editing experience

---

**15.** Using CLI-based alternatives to the new editor takes excessive time "just to adjust 1 or 2 files"

**Source:** [Shopify Community — How to disable the new theme editor](https://community.shopify.com/t/how-to-disable-the-new-theme-editor/552482)
**User:** ScalaApps
**Date:** August 4, 2025

**Key issue:** Neither the new editor nor the CLI workflow is efficient for quick edits

---

## Customization Requires Code (Gap Between Marketing & Reality)

---

**16.** "why is every solution to every answer to add lines of code? I thought the whole point was to not have to worry about being a coder."

**Source:** [Shopify Community — Why does every solution require coding](https://community.shopify.com/t/why-does-every-shopify-solution-require-coding-knowledge/151723)
**User:** davidsamra
**Date:** September 15, 2022

**Key issue:** Shopify marketed as no-code but every customization requires Liquid/HTML knowledge

---

**17.** "if we want a simple change to an invoice template so it shows all of the payments made, and we don't know coding we have to buy an app?"

**Source:** [Shopify Community — Why does every solution require coding](https://community.shopify.com/t/why-does-every-shopify-solution-require-coding-knowledge/151723)
**User:** mom-n-pop
**Date:** November 24, 2024

**Key issue:** Basic template modifications require either coding knowledge or purchasing paid apps

---

**18.** "Literally every other major website editor has a complete drag and drop site builder" — unable to launch business due to inability to complete basic customizations

**Source:** [Shopify Community — Website builder is garbage](https://community.shopify.com/t/shopifys-website-builder-is-garbage-and-our-business-is-suffering-almost-wish-i-never-switched/161168)
**User:** randomperson
**Date:** October 19, 2022

**Key issue:** Needed HTML knowledge for basic tasks like repositioning a Google map; described Shopify's marketing as misleading

---

**19.** "11 years later, I had to dig through basic HTML to resize an image" — compared Shopify unfavorably to Wix ($29/mo + $24-99/mo for PageFly vs. Wix at $27/mo all-in)

**Source:** [Shopify Community — Website builder is garbage](https://community.shopify.com/t/shopifys-website-builder-is-garbage-and-our-business-is-suffering-almost-wish-i-never-switched/161168)
**User:** SamKang
**Date:** November 15, 2023

**Key issue:** Basic visual editing tasks like resizing images require HTML knowledge; competitor platforms handle this natively at lower cost

---

**20.** "Amount of time I spend trying to make simple cosmetic or functional adjustments" — discovering some adjustments are simply impossible

**Source:** [Shopify Community — Website builder is garbage](https://community.shopify.com/t/shopifys-website-builder-is-garbage-and-our-business-is-suffering-almost-wish-i-never-switched/161168)
**User:** Ebbly23
**Date:** April 4, 2024

**Key issue:** Simple visual changes take excessive time and some are flat-out impossible without code

---

**21.** "drag and drop...but once you drag it on there, you can't manually place it where you want"

**Source:** [Shopify Community — Website builder is garbage](https://community.shopify.com/t/shopifys-website-builder-is-garbage-and-our-business-is-suffering-almost-wish-i-never-switched/161168)
**User:** bizzlezx10r
**Date:** July 9, 2024

**Key issue:** Even Shopify's newer page builder tools fail at basic drag-and-drop positioning

---

**22.** "Every time I move or resize the image, I have to reformat the image again...and very often, part of the reformatting won't _take_." ... "I need our blog to have lots of images — and can't imagine fighting this template every time I want to blog."

**Source:** [Shopify Community — Limitations on blog design / Liquid templates](https://community.shopify.com/c/shopify-design/limitations-on-blog-design-creating-custom-liquid-templates/m-p/1693355)
**User:** MasonandCollins
**Date:** August 10, 2022

Community member Ahsan_ANC acknowledged: "Setting up things without coding is difficult"

**Key issue:** Blog image formatting in Liquid templates is broken; changes don't persist, making content creation painful

---

## Key Patterns

### 1. Liquid is fundamentally limited as a language
No object creation, no array manipulation, 50-item loop caps, no custom pagination, no variable scoping/inheritance. Developers repeatedly hit walls that would not exist in any modern templating language.

### 2. No real local development environment
Developers must deploy to see changes. No localhost preview. Slate (the old build tool) was deprecated with no replacement. The CLI workflow is clunky. This makes iteration painfully slow.

### 3. Gap between marketing and reality
Shopify markets itself as no-code/low-code, but nearly every customization requires Liquid or HTML knowledge — or a paid third-party app. Merchants feel misled.

### 4. Theme editor regressions
The new code editor is slower, more complex, and worse for both developers and merchants. No option to revert. Shopify forced an IDE-like experience onto users who just need to tweak a line of code.

### 5. Online Store 2.0 created new problems
Broke section content reuse across templates. The `render` tag doesn't support JSON templates. Developers lost capabilities they had before the "upgrade."

### 6. Cost multiplier from limitations
Because Liquid and the editor can't handle basic tasks, merchants must pay for third-party apps (PageFly at $24-99/mo, etc.) to get visual editing that competitors like Wix include natively at lower total cost.

---

## Amboras Implications

These complaints directly validate the Amboras thesis:

- **AI-native templating** eliminates the need for merchants to learn Liquid or HTML — the platform should handle customization through intent, not code
- **Modern developer tooling** (local dev, hot reload, real programming language) would immediately attract developers frustrated with Liquid's limitations
- **Visual editing that actually works** is table-stakes; Shopify still can't do basic drag-and-drop after 20 years
- **No app tax** — features like invoice customization, image handling, and content reuse should be built in, not sold as add-ons
- **Content reuse and component systems** should be architectural primitives, not afterthoughts that break on major version upgrades
