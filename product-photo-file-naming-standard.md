# Ajeets Robots – Product Photo File Naming Standard

> Version 1.0 — 2026-07-20  
> Companion to: [`product-naming-standard.md`](./product-naming-standard.md)  
> Asset tracker: [Ajeet's Robots Product Photo Asset Plan](https://docs.google.com/spreadsheets/d/163aPWgyV6JHW3HsPz0Jw1sue3Ygm3Zq6g65j7V-7CuE/edit)

All product photography files for Ajeets Robots must follow a single, predictable filename format so assets are easy to identify, sort alphabetically, and hand off between team members.

---

## Filename Format

```
<brand>_<product>_<shot-type>_<sequence>_<date>.<ext>
```

| Segment | Required | Format | Example |
|---------|----------|--------|---------|
| `brand` | Yes | Lowercase, no spaces | `ajeets-robots` |
| `product` | Yes | Lowercase, words separated by hyphens. Normalized per [`product-naming-standard.md`](./product-naming-standard.md) — drop "Classic", fix apostrophes, no special characters | `canvas-wall-art`, `tumbler`, `backpack`, `notebook`, `pet-bowl`, `womens-sneakers` |
| `shot-type` | Yes | Lowercase, one of the approved shot types below | `hero`, `detail`, `lifestyle`, `flat` |
| `sequence` | Yes | Two-digit zero-padded integer, `01`–`99` — increments within the same product + shot type | `01`, `02`, `03` |
| `date` | Yes | `YYYYMMDD` — the date the photo was captured / delivered | `20260720` |
| `ext` | Yes | Lowercase file extension | `jpg`, `png`, `webp` |

**Full example:**

```
ajeets-robots_canvas-wall-art_detail_01_20260720.jpg
│             │                │       │   │
│             │                │       │   └── date: 2026-07-20
│             │                │       └────── sequence: first detail shot
│             │                └────────────── shot type: detail
│             └─────────────────────────────── product: canvas-wall-art
└───────────────────────────────────────────── brand: ajeets-robots
```

---

## Brand Segment

Always:

```
ajeets-robots
```

- Lowercase
- Hyphen between words
- No spaces, no underscores, no apostrophes
- Never `ajeets_robots`, `AjeetsRobots`, `ajeetsrobots`, etc.

---

## Product Segment

The product slug — derived from the official Printify product title per [`product-naming-standard.md`](./product-naming-standard.md):

1. Start with the official product title: `Ajeets Robots - Canvas Wall Art Print`
2. Strip the brand prefix: `Canvas Wall Art Print`
3. Apply product naming standard normalizations:
   - Drop the word **"Classic"** (applied inconsistently across the catalog)
   - Remove possessive apostrophes: `Women's` → `womens`, `Men's` → `mens`
   - Remove extra symbols: `||`, `#1`, quotes, em dashes, etc.
4. Lowercase everything
5. Replace spaces with hyphens
6. Strip any remaining non-alphanumeric characters except hyphens
7. Collapse multiple hyphens into one

| Printify title | → | Photo filename product slug |
|---|---|---|
| `Ajeets Robots - Canvas Wall Art Print` | → | `canvas-wall-art` |
| `Ajeets Robots - Classic Tumbler` | → | `tumbler` |
| `Ajeets Robots \|\| Classic Backpack` | → | `backpack` |
| `Ajeets Robots - Classic Notebook` | → | `notebook` |
| `Pet Bowl` | → | `pet-bowl` |
| `Ajeets Robots - Women's Sneakers` | → | `womens-sneakers` |
| `Ajeets Robots - Classic Mousepad` | → | `mousepad` |
| `Ajeets Robot mens tee` | → | `mens-tee` |
| `Ajeets Robots - Woven Straw Tote` | → | `woven-straw-tote` |
| `Ajeets Robots - Phone Case` | → | `phone-case` |
| `Cork Coaster Set — Minimal "ajeets robots" Logo Drink Coasters (4-Pack)` | → | `cork-coaster-set` |

> **Why normalize?** The Printify catalog contains inconsistent titles (`Classic` on 7 products, double pipes `||`, apostrophes, `#1` suffixes, etc.). The photo filename product slug always uses the cleaned, normalized version so files sort predictably regardless of what the source listing says.

---

## Shot Type Segment

Use one of these approved shot types:

| Shot type | When to use |
|-----------|-------------|
| `hero` | Primary hero / catalog image — clean, front-facing, the image that represents the product |
| `detail` | Close-up of materials, textures, logos, stitching, hardware, print quality |
| `lifestyle` | Product in real-world use — worn, held, in a room, on a person, in context |
| `flat` | Flat lay, top-down, or straight-on studio shot, color-accurate |
| `scale` | Size reference — next to common objects, in hand, with measurements visible |
| `packaging` | Unboxing, shipping box, protective wrap, inserts, tags |
| `variant` | Product variant that's visually different (color, material, finish) from the base — use only when the visual difference matters |

**Do not invent shot types.** If none of the approved types fit, open an issue to discuss adding a new shot type to the standard before using it.

---

## Sequence Number Segment

Two digits, zero-padded: `01`, `02`, `03` … `99`

- Increments **within the same product + shot type**
- Use when you have multiple takes / angles / variants of the same shot type
- Always zero-pad: `01` not `1`

```
ajeets-robots_notebook_hero_01_20260720.jpg   ← first hero shot
ajeets-robots_notebook_hero_02_20260720.jpg   ← second hero shot / alternate angle
ajeets-robots_notebook_detail_01_20260720.jpg  ← first detail shot (pages)
ajeets-robots_notebook_detail_02_20260720.jpg  ← second detail shot (cover texture)
```

---

## Date Segment

`YYYYMMDD` — 8 digits, no separators.

- The date the photo was **captured / delivered**
- Always use UTC / Eastern Time consistently — pick one and stick with it across the entire asset library
- Recommended: Eastern Time (matches the Ajeets Robots team timezone)

```
20260720  ✅
2026-07-20 ❌
20-07-2026 ❌
07202026  ❌
```

---

## File Extension

- Lowercase only: `jpg`, `png`, `webp`
- No uppercase: `JPG`, `PNG` ❌
- No `.jpeg` — normalize to `.jpg`

---

## Full Rules Summary

| Rule | ✅ Correct | ❌ Incorrect |
|------|-----------|-------------|
| All lowercase | `ajeets-robots_notebook_hero_01_20260720.jpg` | `Ajeets-Robots_Notebook_Hero_01_20260720.JPG` |
| Segments separated by single underscores | `ajeets-robots_tumbler_detail_01_20260720.jpg` | `ajeets-robots-tumbler-detail-01-20260720.jpg` |
| Product slug is normalized (no "Classic", no apostrophes) | `womens-sneakers` | `womens-sneakers-classic`, `women's-sneakers` |
| Shot type from approved list only | `hero`, `detail`, `lifestyle`, `flat`, `scale`, `packaging`, `variant` | `closeup`, `beauty`, `glam` |
| Sequence is zero-padded, 2 digits | `01`, `02`, `12` | `1`, `2`, `001` |
| Date is `YYYYMMDD`, no separators | `20260720` | `2026-07-20`, `07202026` |
| Extension is lowercase | `.jpg`, `.png`, `.webp` | `.JPG`, `.jpeg` |
| No spaces anywhere in filename | `pet-bowl_detail_01_20260720.jpg` | `pet bowl_detail_01_20260720.jpg` |
| No duplicate meaning across segments | `backpack_hero_01_20260720.jpg` | `backpack_backpack_hero_01_20260720.jpg` |

---

## Examples

### Single product — multiple shots

```
ajeets-robots_canvas-wall-art_hero_01_20260720.jpg
ajeets-robots_canvas-wall-art_detail_01_20260720.jpg
ajeets-robots_canvas-wall-art_detail_02_20260720.jpg
ajeets-robots_canvas-wall-art_lifestyle_01_20260720.jpg
ajeets-robots_canvas-wall-art_flat_01_20260720.jpg
```

### Multiple products — same shot type (sorts cleanly)

```
ajeets-robots_backpack_hero_01_20260720.jpg
ajeets-robots_notebook_hero_01_20260720.jpg
ajeets-robots_pet-bowl_hero_01_20260720.jpg
ajeets-robots_tumbler_hero_01_20260720.jpg
```

### Variants with sequence numbers

```
ajeets-robots_womens-sneakers_hero_01_20260720.jpg   ← side profile
ajeets-robots_womens-sneakers_hero_02_20260720.jpg   ← top-down
ajeets-robots_womens-sneakers_detail_01_20260720.jpg ← material close-up
ajeets-robots_womens-sneakers_detail_02_20260720.jpg ← sole tread
ajeets-robots_womens-sneakers_lifestyle_01_20260720.jpg
```

---

## Mapping to the Photo Asset Plan

The [Ajeet's Robots Product Photo Asset Plan](https://docs.google.com/spreadsheets/d/163aPWgyV6JHW3HsPz0Jw1sue3Ygm3Zq6g65j7V-7CuE/edit) spreadsheet uses a simplified filename column (`product_shot-type_detail.jpg`) without the brand prefix, sequence number, or date — this is intentional for readability in the planning sheet.

**When saving final delivered assets**, always use the full format:

```
<planning-filename> → <final-filename>
canvas-wall-art_detail_texture-frame.jpg
  → ajeets-robots_canvas-wall-art_detail_01_20260720.jpg
```

---

## Revision History

| Version | Date | Changes |
|---|---|---|
| 1.0 | 2026-07-20 | Initial standard. Format: `<brand>_<product>_<shot-type>_<sequence>_<date>.<ext>`. Defined 7 approved shot types (hero, detail, lifestyle, flat, scale, packaging, variant). Aligned product slug normalization with `product-naming-standard.md`. |
