---
title: Food blocks and metafields
---

Mortar's product page has four food blocks. Each can show the same text on every product, or a different value per product through **metafields** connected as dynamic sources.

| Block | What it shows | Suggested metafield |
|---|---|---|
| Profile meter | Up to 5 scales from 0 to 5, such as body, acidity and sweetness | Integer metafields `custom.profile_1` to `custom.profile_5` |
| Nutrition table | A nutrition table with a caption and two value columns | Multi-line text `custom.nutrition`, one row per line: `Energy | 1650 kJ | 495 kJ`. Start a line with `- ` for a sub-row such as "of which sugars". |
| Allergens | "Contains" and "May contain" lists with icons for the 14 EU allergens | Single line text `custom.allergens`, comma-separated: `Milk, Sesame` |
| Origin facts | A row of up to 6 facts such as region, producer, altitude and process | Single line text metafields such as `custom.origin`, `custom.producer` |

**To create a metafield:** Settings > Custom data > Products > Add definition. **To connect it:** open a product page in the theme editor, select the block, and use the dynamic source icon next to the setting.

Empty values hide themselves: a product without nutrition rows shows no nutrition table, and a fact without a value is left out.

**Label band on product cards:** Theme settings > Product cards > Label band shows the origin, the first tasting note and the variant weight under each card. Enter the metafields to read as `namespace.key`, for example `custom.origin`.

**Recipes:** create a blog post and choose the `recipe` template. The recipe facts, ingredients and method blocks can also connect to article metafields. Mortar adds Recipe structured data so search engines can show your recipe.
