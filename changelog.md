---
title: Changelog
---

All notable changes to Mortar are documented here. This project follows semantic versioning.

### 0.13.6 — Origin facts wrapping

### Fixed
- Origin facts no longer break words in the middle (for example "cooperati-ve") in narrow product columns. Facts wrap onto a second row first, and words break only when a single word is wider than its column.

### 0.13.5 — Page width overflow

### Fixed
- Home pages with the Tasting flight section scrolled sideways on phones. Hidden labels inside the scrolling list stretched the page; the list now contains them. The same guard is added to the blog posts and complementary products carousels and the collection tabs.

### 0.13.4 — Recipe page overlap

### Fixed
- Recipe pages: the ingredients box no longer sticks while scrolling, which made it slide over the notes and the "Shop this recipe" products below it.

### 0.13.3 — Transparent header scope

### Changed
- The transparent header now applies only over a full-width image banner or a slideshow. Over a split banner it would put light text on a light background.
- The free shipping minimum setting shows only when the free shipping bar is on.

### 0.13.2 — Store test fixes

### Fixed
- Transparent header: its text and icon colors now come from the chosen color scheme (they were empty).
- Pop-up, age verifier and product pop-up dialogs are centered on screen again.
- The pop-up waits for the age verifier to close instead of skipping its turn.
- In the theme editor, the pop-up and age verifier open as soon as they are added or edited.
- Recently viewed keeps the page margins.
- Every private block now has a preset, so merchants can add (or re-add) columns, slides, testimonials, collection tabs, product blocks and the rest from the block picker. Columns and slides start with sample content.

### 0.13.1 — Theme editor color schemes

### Fixed
- Every color scheme in `config/settings_data.json` now includes `background_gradient`. Without it, the theme editor said no color schemes were defined and would not preview changes.

### 0.13.0 — New sections and more settings

### Added
- Sections: Scrolling text, Countdown timer, Before and after, Timeline, Image grid, Collection tabs, Recently viewed, Pop-up, Age verifier.
- Product blocks: Rating (reads the standard reviews metafields), Quick order list, Pop-up link. Footer block: Logo.
- Sticky add to cart bar on product pages (off, all devices, or mobile only).
- Free shipping progress bar in the cart and cart drawer.
- Load more button and infinite scroll on collection and search pages.
- Combined listings: picking an option that belongs to a sibling product swaps the page in place.
- Transparent header over a first-section image banner or slideshow on the home page.
- Product gallery: mobile layout, aspect ratio and image fit settings.
- Theme settings: heading case and letter spacing, button size, card style, card text alignment, image zoom on hover, ratings on cards.
- More settings in most sections: heading size, mobile layout (grid or carousel), column style and alignment, image ratio, content style, mobile image position, slideshow mobile height, hero content box, footer copyright text and social icons, announcement bar text size and social icons, and more.
- New icons: star, shield, return, chat, award, coffee.

### Changed
- The variant picker moved to its own module (`assets/variant-picker.js`) so the product form stays small.

### 0.12.5 — Safer default links

### Fixed
- Default buttons for "Our story" and "Read the story" now link to the catalog instead of `/pages/about`, which returns a 404 on a store without an About page.

### 0.12.4 — Default button links

### Fixed
- Demo buttons in the home templates (hero, shelf promo, origin story) had no link, so they rendered as disabled-looking, half-faded buttons. They now link to the catalog or the About page by default in every preset.

### 0.12.3 — Preview fixes 2

### Fixed
- Cart requests: Shopify answers `/cart/add.js` and the other `.js` cart endpoints as `text/javascript`, so the response was read as text. Add to cart, quantity changes and remove did not update the drawer, the cart page or the header count. JSON is now detected for those responses.
- Origin facts block: the placeholder text ("Add a region" and similar) no longer shows to shoppers. The settings have no default, so the strip stays hidden until a value or dynamic source is set (Shopify rejects an empty `default`, which stopped templates using the block from uploading in 0.12.2).

### 0.12.1 — Preview fixes

### Fixed
- Header: the bottom border covered only half the page width because the header wrapper shared the `section-header` class with section headings. The wrapper class is now `site-header`.

### 0.12.0 — M12 requirements check and package

### Added
- Custom Liquid block in the footer, apps and email signup sections (every place that accepts app blocks).
- Quick add shows the full media gallery (images, videos, 3D models).
- Skeleton license notice in the layout, so it ships inside the theme zip.
- Requirements checklist (docs/01) marked against the code, with open items labelled store or human; uniqueness statement in docs/DECISIONS.md.

### Checked
- `shopify theme package` builds a zip with `/listings/mortar`, `/listings/roast`, `/listings/crumb`, no `config/markets.json`, no docs, demo files or scripts.

### 0.11.0 — M11 documentation and listing

### Added
- `docs-site/`: documentation site content (not part of the theme zip): getting started, presets, food blocks and metafields, subscriptions, local pickup and preferred date, right-to-left languages, translations, performance tips, updating, FAQ, support policy and contact form fields.
- `docs-site/theme-settings.md`, `sections.md`, `blocks.md`: generated from the theme's schemas by `scripts/build-docs-reference.mjs`, so setting names always match the editor.
- `docs-site/listing.md`: listing form copy, feature tags checked against the theme, screenshot plan, testing instructions and review notes.

### Fixed
- The Scroll animations setting now works: sections that start below the fold fade in as they enter the screen (never the first screen, off in the editor and for reduced motion).

### 0.10.0 — M10 demo store content

### Added (demo content, not part of the theme zip)
- `demo/mortar-products.csv` (24 products + gift card), `demo/roast-products.csv` (16 + gift card), `demo/crumb-products.csv` (10 + gift card): original descriptions, variants, prices, sale prices, SKUs, weights, inventory (sold-out variants and one sold-out product), unit prices, `new` tags, collection tags and product metafields.
- `demo/*-image-map.csv`: which image goes on which product.
- `demo/README.md` (store setup steps and feature coverage), `demo/metafields.md` (definitions and dynamic source connections), `demo/menus.md` (three-level menus with mega menu promos), `demo/content-*.md` (pages, recipe posts, journal posts, theme editor copy, password messages), `demo/mortar-arabic.csv` (Arabic copy for Translate & Adapt).
- `demo-logos/`: SVG wordmarks for Sumac Lane Provisions, Ninth Hill Coffee and Oven Gate Bakehouse.

### 0.9.0 — M9 performance and accessibility pass

### Changed
- Removed reduced opacity from readable text (compare-at prices, unit prices, tax notes, filter counts, consent note, origin fact labels, quote roles, list markers) so it keeps the scheme's full contrast; sold-out variant options now use a dashed border plus strike-through instead of faded text.
- Product and collection links prefetch on hover (speculation rules; off in the theme editor).

### Added
- `scripts/check-html-balance.mjs`: checks that opening and closing tags balance in every Liquid file; runs in `npm test` and CI.

### Checked (static)
- LCP: hero image eager with high fetch priority; first product media eager; first two collection cards eager; everything else lazy with width and height.
- Render-blocking CSS: base 7.3 KB + components 17.7 KB + rich text 1.5 KB (unminified); section and block styles are subset per page by Shopify.
- JavaScript: native modules, largest file 9.6 KB; home page first load about 20–25 KB unminified; product, cart, filters, quick add, pickup, recommendations and predictive search load only where used or on interaction.
- Accessibility: one visible main navigation landmark at a time, labelled controls, focus traps and focus return for drawers and dialogs, live regions for cart, filters and search, 44 px targets for primary controls.

### 0.8.0 — M8 presets and listings

### Added
- `/listings/mortar`, `/listings/roast`, `/listings/crumb`: home, product, collection, about and recipe templates plus header and footer groups for each preset (docs/11). Mortar matches the root templates.
- Roast: full-height hero, subscription promo, tasting flight (body, acidity, sweetness), coffee carousel, producer origin story, brew bar lookbook, brew guides, journal, newsletter; product page with roast profile (body, acidity, sweetness, roast), origin facts (region, producer, altitude, process, varietal) and subscription selected by default.
- Crumb: scalloped hero, pickup banner, eight-item menu shelf, custom cakes, ordering FAQ, testimonials, newsletter; product page with pickup near the top, allergens and a collapsed nutrition table; preferred date and cutoff message on in the cart.
- Hero background video (uploaded video, muted, looped, with a pause button; image shows first and for reduced motion).
- Nutrition table option to show in a collapsible row.
- `scripts/validate-templates.mjs` checks every section type, block type, nesting rule and setting ID in templates, section groups and listings; runs in `npm test` and CI.

### Fixed
- Nutrition rows were treated as sub-rows whenever the name contained a hyphen; only rows starting with "- " are sub-rows now.

### 0.7.0 — M7 locales and right-to-left

### Added
- Storefront translations: Arabic (with zero, two, few and many plural forms), Hebrew, French, German, Spanish, Italian, Dutch and Brazilian Portuguese (233 strings each, placeholders checked).
- Arabic editor translations (`ar.schema.json`, 652 strings).
- `scripts/unused-translation-keys.mjs` lists (and with `--fix` removes) translation keys no file uses.

### Removed
- 94 unused Skeleton translation keys.

### Checked
- Right-to-left review: drawers and sliding panels use `--dir-sign`; carousels, gallery and slideshow keys mirror; directional icons flip; hotspots stay on their image position; prices, SKUs, phone numbers and gift card codes are bidi-isolated; Arabic gets no letter-spacing, no forced uppercase and no italics.

### 0.6.0 — M6 content templates and signature sections

### Added
- Blog page (grid or list, columns, posts per page, tag filter, card options for image, ratio, shape, date, author, comment count, excerpt) and article card snippet.
- Blog post (content width, alignment, featured image ratio and shape, date, author, tags, share, comments with pagination, moderation and error messages, app blocks).
- Recipe template (article.recipe): recipe facts, ingredients beside numbered method steps, notes, "Shop this recipe" products, comments, Recipe structured data built from the blocks.
- Page section with blocks; contact form (name, email, phone, message, success and errors); 404 page with search; password page (logo or store name, password message, email signup, storefront password form, background image); gift card page (logo or name, balance, expiry, code that never clips, QR code 160 px, copy, print, Apple Wallet).
- Signature sections: origin story (shaped image beside provenance blocks and origin facts), ritual (recipe teaser with recipe facts and "Shop this recipe"), pickup banner (address, hours, static map image), subscription promo (steps and a product with selling plans), lookbook (image with up to 6 product hotspots using native popovers).
- Templates: blog, article, article.recipe, page, page.contact, page.faq (with FAQ data), page.about, 404, password; product template gains origin story and ritual; home template is the full Mortar install state (hero, shelf, origin story, tasting flight, gifting, ritual, subscription promo, testimonials, journal, email signup).

### Removed
- Skeleton 404, article, blog, page and password sections.

### 0.5.0 — M5 collection, search, cart

### Added
- Collection page: banner (title, description, optional shaped image, alignment), breadcrumbs, filters and sorting (sidebar or drawer layout), product grid with shelf lines, columns for large and small screens, products per page (8–24), pagination, empty states for empty collections and for filters with no matches.
- Filters: list, boolean, price range and swatch/image filters, active filter pills, Clear all; one GET form that works without JavaScript; facets.js applies changes without reloading, updates the URL and announces the result count.
- Collections list page (sort, columns, ratio, shape, product counts, image fallbacks) and search results page (mixed products, articles and pages, filters, sorting, no-results message).
- Featured collection (grid or carousel, heading, subheading, View all, placeholder cards), shelf (products and promo tiles that span two columns), tasting flight (2–4 products on three shared scales with add to cart).
- Cart page and cart drawer sharing line item and summary snippets: options, properties, selling plan, unit price, line and order discounts, quantity rules, remove, order note, preferred date, cutoff message, totals and tax note, checkout and accelerated checkout buttons; empty states; complementary products in the drawer.
- cart.js: quantity changes re-render every cart section and the header count; errors show next to the line; note and preferred date save automatically; the cart button opens the drawer.
- Product carousel component (slider-component) with mirrored direction in right-to-left.
- Templates: collection.json, list-collections.json, search.json, cart.json.

### Removed
- Skeleton collection, collections, search and cart sections.

### 0.4.0 — M4 product

### Added
- Main product section where every element is a block: title, vendor, price (sale badge, unit price, tax note), SKU, real inventory status, variant picker (buttons, swatches, dropdown), quantity (quantity rules, volume pricing), buy buttons, pickup availability, description, share, complementary products, plus content blocks and app blocks. Layout settings: media position, media layout (stacked, two columns, thumbnails), media width, sticky information, zoom, hide other variants' media, framed label style, color scheme, padding.
- Subscribe-first buy box: one-time and subscription cards with per-plan price, savings and per-delivery price, from any subscription app's selling plans.
- Gift card recipient form (email, name, message, send date, timezone offset) with field errors.
- Shop Pay Installments and accelerated checkout buttons (on by default, Shopify colors).
- Media gallery: images, uploaded video, YouTube/Vimeo, 3D models with View in your space; first media eager; selected variant's media first; swipe counter on small screens; zoom dialog.
- Food blocks: profile meter (5 accessible meters), nutrition table (semantic table from 'Name | per 100 g | per serving' lines), allergens (contains / may contain with 14 EU allergen icons), origin facts (provenance strip).
- Featured product section with the same blocks; pickup availability section and drawer; related products section; quick add dialog section.
- Product card snippet (die-cut media, badges, label band, swatches, hover image, quick add).
- JS: product-form.js (variant changes through the Section Rendering API, add to cart), gallery.js, pickup.js, recommendations.js, quick-add.js; on-demand module loading in global.js.
- Templates: product.json (Mortar default), product.gift-card.json.

### Removed
- Skeleton product section.

### 0.3.0 — M3 building blocks and content sections

### Added
- Blocks: heading, text, eyebrow, button, image (4 shapes, ratios), video, icon with text, spacer, divider, group (stack, row, grid; custom scheme; background image), collapsible row, quote, logo list (+ logo), breadcrumbs (with BreadcrumbList data), custom Liquid; email signup, social icons and Follow on Shop from M2.
- Sections: hero (full width or image beside content; eager LCP image; mobile image), slideshow (up to 10 slides, independent autoplay with pause), image with text, rich text, multicolumn, collapsible content (optional FAQ data), video (uploaded, YouTube, Vimeo), email signup, logo list, testimonials, blog posts, collection list, custom Liquid, apps.
- `media.js`: deferred video player, autoplay pause button, slideshow component (scroll-snap, mirrored arrow keys in right-to-left).
- Snippets: `art-image` (separate mobile image), `video-player`.
- Home template (Mortar default install): hero, image with text, multicolumn, testimonials, blog posts, email signup.

### Removed
- Skeleton `custom-section` section.

### 0.2.0 — M2 header, footer, navigation

### Added
- Announcement bar section: up to 6 announcements, previous/next buttons and optional rotation with a pause button (pauses on hover and focus; off in the theme editor and for reduced motion).
- Header section built from static blocks: logo, menu, search, country and language, account (`<shopify-account>`, visible on mobile and desktop) and cart with live count. Three layouts, sticky options (none, always, on scroll up), bottom border, color schemes.
- Desktop menu up to 3 levels, as dropdowns or a mega menu with up to 2 promo blocks per top-level item.
- Mobile menu drawer with 3 sliding levels, back buttons, focus trap and Escape stepping back one level; account and localization at the bottom. Works as an accordion without JavaScript.
- Predictive search (ARIA combobox) for products, collections, pages, articles and suggestions; loads on first focus.
- Country/region and language selectors as popover listboxes ("Germany (EUR €)" format), with native selects and an Update button without JavaScript.
- Footer section: menu, text, email signup, social media icons and Follow on Shop blocks (max 6, plus app blocks); bottom bar with localization, payment icons, copyright, policy links and `powered_by_link`; optional background pattern; back-to-top link.
- JS modules: `header.js`, `announcement-bar.js`, `predictive-search.js`, `localization.js`.
- `scripts/list-translation-keys.mjs`: lists translation keys used in code but missing from the English locale files.

### 0.1.0 — M1 foundations

### Added
- Global settings (`config/settings_schema.json`): logo and favicon, colors (11-role color scheme group), typography, layout, shapes, buttons, product cards, badges, cart, search, social media, navigation aids, animations, currency format. All labels in `locales/en.default.schema.json`.
- Mortar, Roast and Crumb global presets in `config/settings_data.json` (5 color schemes each).
- Design tokens (`snippets/css-variables.liquid`), font faces with bold/italic variants (`snippets/font-faces.liquid`), RTL font fallback stack and Arabic typography rules.
- `assets/base.css` (reset, type, layout primitives, utilities), `assets/components.css` (buttons, fields, stamps, label band, profile meter, die-cut shapes, patterns, price, quantity, disclosure, dialogs and drawers), `assets/rte.css`.
- Original icon set (`snippets/icon.liquid`, 60+ icons incl. 14 allergens and 12 social), decorative patterns (`assets/pattern-*.svg`).
- `layout/theme.liquid` and `layout/password.liquid` with `lang` + `dir`, skip link, live region, import map, body font preload.
- Core JS modules: `global.js` (helpers, focus trap, quantity input, share button, scroll reveal), `fetch.js`, `dialog.js` (native dialog modal and drawer).
- `snippets/image.liquid` (responsive `image_tag` wrapper with LCP priority), `snippets/meta-tags.liquid` (OG, X card, product and article structured data).
- Dev scripts: `scripts/contrast-check.mjs`, `scripts/lint-physical-css.mjs`; CI runs both.

### Removed
- Skeleton demo files: `hello-world` section, `critical.css`, Skeleton SVG icons.

### Unreleased (M0)
- Scaffolded from the Shopify Skeleton theme (MIT).
- Theme Check config, `.shopifyignore`, and CI workflow.
