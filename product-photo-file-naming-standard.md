# Ajeets Robots – Product Photo File Naming Standard

> Version 1.1 — 2026-07-20  
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

For edited derivatives, an optional edit suffix is appended after the date, before the extension (see [Edited-Image Suffixes](#edited-image-suffixes)):

```
<brand>_<product>_<shot-type>_<sequence>_<date>-<edit>.<ext>
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

## Filename Component Rules

### Spaces

Spaces are **forbidden everywhere** in photo filenames — brand, product, shot type, sequence, date, extension, and edit suffixes.

- Spaces break URLs when assets are served from CDNs or linked in emails
- Spaces break shell scripts, Makefiles, and CI/CD pipelines (`rm my file.jpg` → tries to delete two files)
- Spaces cause double-encoding bugs (` ` → `%20` → `%2520`)
- Spaces sort inconsistently across operating systems (macOS ignores them, Linux doesn't)

**Rule:** If a source file arrives with spaces in the name, rename it to the standard format immediately before committing to the asset library. Never commit a file with spaces in its name.

| Segment | ✅ Correct | ❌ Incorrect | Why it fails |
|---------|-----------|-------------|-------------|
| Brand | `ajeets-robots` | `ajeets robots` | space in brand segment |
| Product | `pet-bowl` | `pet bowl` / `pet_bowl` | space / underscore in product slug — use hyphens only |
| Shot type | `lifestyle` | `life style` / `life-style` | spaces not allowed; shot types are single words, no hyphens |
| Entire filename | `ajeets-robots_notebook_hero_01_20260720.jpg` | `ajeets-robots notebook hero 01 20260720.jpg` | spaces between every segment — breaks everything |
| Edit suffix | `…_20260720-r1.jpg` | `…_20260720 - r1.jpg` | space before edit suffix |

### Capitalization

**All lowercase, always, every character** — brand, product, shot type, extension, and edit codes.

- Lowercase filenames sort identically on case-sensitive (Linux) and case-insensitive (macOS/Windows) filesystems
- Mixed case causes duplicate-file collisions in Git: `Tumbler.jpg` and `tumbler.jpg` are the same file on macOS but two different files on Linux
- Uppercase extensions (`.JPG`, `.PNG`) break case-sensitive web servers and CDNs
- No Title Case, camelCase, PascalCase, SCREAMING_SNAKE_CASE, or any other capitalization scheme

| ✅ Correct | ❌ Incorrect | Style that was incorrectly used |
|-----------|-------------|-------------------------------|
| `ajeets-robots_notebook_hero_01_20260720.jpg` | `Ajeets-Robots_Notebook_Hero_01_20260720.JPG` | Title Case + uppercase extension |
| `womens-sneakers` | `WomensSneakers` | PascalCase |
| `pet-bowl` | `petBowl` | camelCase |
| `tumbler_detail_01_20260720.jpg` | `TUMBLER_DETAIL_01_20260720.JPG` | SCREAMING_SNAKE_CASE |
| `backpack_lifestyle_01_20260720.jpg` | `Backpack_Lifestyle_01_20260720.jpg` | Title Case segments |

### Special Characters

**Allowed characters only:** lowercase letters `a–z`, digits `0–9`, hyphen `-`, underscore `_`, period `.`

- Hyphens (`-`) — **within segments only**, to separate words in the brand and product slugs: `ajeets-robots`, `canvas-wall-art`, `womens-sneakers`
- Underscores (`_`) — **between segments only**, to separate brand / product / shot-type / sequence / date: `ajeets-robots_canvas-wall-art_detail_01_20260720.jpg`
- Period (`.`) — **once only**, immediately before the file extension: `.jpg`
- That's it. Nothing else.

**Banned characters — strip/replace all of these before building the filename:**

| Character(s) | How to handle | Example |
|---|---|---|
| Space ` ` | Replace with hyphen `-` | `pet bowl` → `pet-bowl` |
| Apostrophe / single quote `'` / `’` | Delete | `Women's` → `womens` |
| Double quote `"` | Delete | `"ajeets robots"` → `ajeets-robots` |
| Pipe `\|` / slash `/` / backslash `\` | Delete | `Ajeets Robots \|\| Backpack` → `backpack` |
| Ampersand `&` | Replace with `and` | `salt & pepper` → `salt-and-pepper` |
| Parentheses `()` / brackets `[]` / braces `{}` | Delete all, including contents if it's a size/quantity note that belongs in metadata not the filename | `Coasters (4-Pack)` → `coasters` |
| Hash / number sign `#` | Delete | `Sweatshirt #1` → `sweatshirt` |
| Em dash `—` / en dash `–` | Replace with hyphen `-` | `Coaster Set — Minimal` → `coaster-set-minimal` |
| Period `.` | Delete, except the single period before the file extension | `v1.2` → `v12` (but don't use version numbers anyway — see below) |
| Comma `,` / colon `:` / semicolon `;` | Delete | — |
| Exclamation / question `!` `?` | Delete | — |
| At sign `@` / dollar `$` / percent `%` / plus `+` / equals `=` / tilde `~` | Delete | — |
| Accented / non-ASCII characters | Transliterate to ASCII | `café` → `cafe`, `naïve` → `naive`, `jalapeño` → `jalapeno` |

**Product slug normalization — full worked example:**

```
Source Printify title:
  Cork Coaster Set — Minimal "ajeets robots" Logo Drink Coasters (4-Pack)

Step by step:
  1. Strip brand prefix →  (none in this case, brand is embedded in quotes)
  2. "Classic" → N/A
  3. Remove quotes: "ajeets robots" → ajeets robots
  4. Em dash → hyphen: — → -
  5. Parentheses → delete: (4-Pack) → [removed]
  6. Lowercase: cork coaster set - minimal ajeets robots logo drink coasters
  7. Spaces → hyphens: cork-coaster-set---minimal-ajeets-robots-logo-drink-coasters
  8. Collapse multiple hyphens: cork-coaster-set-minimal-ajeets-robots-logo-drink-coasters
  9. Trim to meaningful product name: cork-coaster-set

Final photo filename product slug:  cork-coaster-set
Full filename:  ajeets-robots_cork-coaster-set_hero_01_20260720.jpg
```

### Version Numbers

**Do not put version numbers in photo filenames.**

- The **sequence number** (`01`, `02`, …) is the versioning mechanism for alternate takes/angles within a shot type — that is your "version"
- Do NOT add `v1`, `v2`, `v3`, `ver2`, `final`, `final_v2`, `approved`, `use-this-one`, etc. anywhere in the filename
- If a photo is re-edited / re-graded / re-cropped after delivery, use the **edited-image suffix** (see below) — do not bump the sequence number and do not add a version number
- The sequence number is assigned at capture/delivery time and never changes for a given image. It identifies *which take*, not *which edit*
- Need more than 99 takes of the same shot type? Open an issue — you probably need to split the shoot, not extend the sequence field

| ✅ Correct | ❌ Incorrect | Why |
|---|---|---|
| `ajeets-robots_tumbler_hero_01_20260720.jpg` | `ajeets-robots_tumbler_hero_v1_01_20260720.jpg` | version number in filename — the sequence `01` *is* the version |
| `ajeets-robots_tumbler_hero_02_20260720.jpg` | `ajeets-robots_tumbler_hero_01_v2_20260720.jpg` | don't version the sequence — `02` is the next take |
| *(use edited suffix, see below)* | `ajeets-robots_tumbler_hero_01_final_20260720.jpg` | "final" is a version label — use edit suffix rules |
| `ajeets-robots_notebook_detail_03_20260720.jpg` | `ajeets-robots_notebook_detail_v3_20260720.jpg` | shot 3 of the detail set is `03`, not `v3` |

### Edited-Image Suffixes

When a delivered photo is edited after the fact (color correction, retouching, cropping, resizing, background removal, etc.), append an **edit suffix** between the date and the file extension.

**Format:** `-<edit-code><n>`

Where `<edit-code>` is a short lowercase tag from the approved list below, and `<n>` is an incrementing digit starting at `1` for each additional pass of that edit type.

**Approved edit codes:**

| Code | Meaning | Example |
|------|---------|---------|
| `r` | Retouched / color-corrected | `…_20260720-r1.jpg` |
| `c` | Cropped / reframed | `…_20260720-c1.jpg` |
| `bg` | Background removed / replaced | `…_20260720-bg1.jpg` |
| `rs` | Resized / web-optimized | `…_20260720-rs1.jpg` |

**Rules:**

- Chain multiple edits by concatenating codes **in the order applied**: `…_20260720-r1-c1.jpg` = retouched, then cropped. `…_20260720-bg1-rs1.jpg` = background removed, then resized
- Increment the trailing digit for each additional pass of the same edit type: `r1` → `r2` → `r3`
- **Never modify the base filename** (brand / product / shot-type / sequence / date) when creating an edited derivative — only append the edit suffix
- The unedited original always exists without a suffix — this is the source of truth
- Do not use freeform suffixes like `-final`, `-edit`, `-v2`, `-approved`, `-use-this-one`, `-client-approved` — use the approved edit codes only
- Edit suffixes go **after the date, before the extension**, with a leading hyphen: `…_20260720-r1.jpg` ✅ not `…-r1_20260720.jpg` ❌

| ✅ Correct | ❌ Incorrect | Why |
|---|---|---|
| `ajeets-robots_notebook_hero_01_20260720-r1.jpg` | `ajeets-robots_notebook_hero_01_20260720_final.jpg` | "final" is not an approved edit code — use `r1` |
| `ajeets-robots_pet-bowl_detail_02_20260720-bg1-rs1.jpg` | `ajeets-robots_pet-bowl_detail_02_20260720_bg_removed_resized.jpg` | freeform suffix — use `bg1-rs1` |
| `ajeets-robots_tumbler_hero_01_20260720-r2.jpg` | `ajeets-robots_tumbler_hero_01_v2_20260720.jpg` | version prefix in wrong place — use `-r2` edit suffix after the date |
| `ajeets-robots_backpack_lifestyle_01_20260720.jpg` | *(original, no suffix — this is correct)* | unedited originals have no suffix — that file is the source of truth |
| `ajeets-robots_sneakers_detail_01_20260720-r1-c1.jpg` | `ajeets-robots_sneakers_detail_01_20260720-retouched-cropped.jpg` | full words — use short codes `r1-c1` |
| `ajeets-robots_canvas-wall-art_hero_01_20260720-bg1.jpg` | `ajeets-robots_canvas-wall-art_hero_01_bg_20260720.jpg` | edit suffix must come after the date, not before |

---

## Correct Filename Examples

Twelve correct filenames from the Ajeets Robots Printify catalog, covering all six products in the [Photo Asset Plan](https://docs.google.com/spreadsheets/d/163aPWgyV6JHW3HsPz0Jw1sue3Ygm3Zq6g65j7V-7CuE/edit):

### Canvas Wall Art Print — Home

| # | Filename | Shot description |
|---|----------|-----------------|
| 1 | `ajeets-robots_canvas-wall-art_hero_01_20260720.jpg` | Hero — wall-mounted, straight-on, styled room |
| 2 | `ajeets-robots_canvas-wall-art_detail_01_20260720.jpg` | Detail — canvas weave + pine frame edge, 1.25" gallery wrap |

### Classic Tumbler — Gifts

| # | Filename | Shot description |
|---|----------|-----------------|
| 3 | `ajeets-robots_tumbler_hero_01_20260720.jpg` | Hero — ¾ angle, lid on, neutral background |
| 4 | `ajeets-robots_tumbler_detail_01_20260720.jpg` | Detail — Ajeets Robots print/logo, stainless steel finish |

### Classic Backpack — Travel

| # | Filename | Shot description |
|---|----------|-----------------|
| 5 | `ajeets-robots_backpack_hero_01_20260720.jpg` | Hero — front-facing, zipped closed |
| 6 | `ajeets-robots_backpack_detail_01_20260720.jpg` | Detail — main compartment open, padded laptop sleeve, 13L capacity |

### Classic Notebook — Work & Study

| # | Filename | Shot description |
|---|----------|-----------------|
| 7 | `ajeets-robots_notebook_hero_01_20260720.jpg` | Hero — closed, cover design front-facing |
| 8 | `ajeets-robots_notebook_detail_01_20260720.jpg` | Detail — open to dotted pages, 89 g/m² paper, Wire-O binding lays flat |

### Pet Bowl — Pets

| # | Filename | Shot description |
|---|----------|-----------------|
| 9 | `ajeets-robots_pet-bowl_hero_01_20260720.jpg` | Hero — top-down, design visible, neutral background |
| 10 | `ajeets-robots_pet-bowl_detail_01_20260720.jpg` | Detail — ceramic glazed finish, 16oz / 6" diameter × 2.25" tall |

### Women's Sneakers — Apparel

| # | Filename | Shot description |
|---|----------|-----------------|
| 11 | `ajeets-robots_womens-sneakers_hero_01_20260720.jpg` | Hero — side profile, pair, white background |
| 12 | `ajeets-robots_womens-sneakers_lifestyle_01_20260720.jpg` | Lifestyle — on-foot, casual/streetwear context |

All 12 filenames follow the standard exactly:
- ✅ all lowercase
- ✅ segments separated by single underscores
- ✅ product slugs normalized per `product-naming-standard.md` (`tumbler` not `classic-tumbler`, `womens-sneakers` not `women's-sneakers`)
- ✅ approved shot types only (`hero`, `detail`, `lifestyle`)
- ✅ zero-padded 2-digit sequence
- ✅ `YYYYMMDD` date
- ✅ lowercase `.jpg` extension
- ✅ no spaces, no special characters, no version numbers

---

## Incorrect Filename Examples

Six real-world mistakes drawn from the Ajeets Robots Printify catalog — what **not** to do, and why:

| # | ❌ Incorrect filename | What's wrong | ✅ Correct version |
|---|---------------------|-------------|-------------------|
| 1 | `Ajeets-Robots_Notebook_Hero_01_20260720.JPG` | **Capitalization** — Title Case brand/product/shot-type + uppercase `.JPG` extension. Breaks case-sensitive filesystems and CDNs. | `ajeets-robots_notebook_hero_01_20260720.jpg` |
| 2 | `ajeets-robots_women's-sneakers_detail_01_20260720.jpg` | **Special characters** — apostrophe in product slug (`women's`). Apostrophes break URLs, break shell scripts, and cause encoding bugs. Per `product-naming-standard.md`, `Women's` → `womens`. | `ajeets-robots_womens-sneakers_detail_01_20260720.jpg` |
| 3 | `ajeets-robots Classic Tumbler _ hero _ 1 _ 20260720.jpg` | **Spaces everywhere** — spaces in product slug, spaces around underscores, unpadded sequence number. Breaks URLs, shell scripts, CI/CD. | `ajeets-robots_tumbler_hero_01_20260720.jpg` |
| 4 | `ajeets-robots_backpack_hero_v2_20260720.jpg` | **Version number in the wrong place** — `v2` is not part of the standard. The sequence number IS the versioning mechanism — this should be `hero_02_…`. Also missing the required 2-digit sequence field (should be `hero_02_…`, not `hero_v2_…`). | `ajeets-robots_backpack_hero_02_20260720.jpg` |
| 5 | `ajeets-robots_pet-bowl_detail_01_20260720_final-edit.jpg` | **Freeform edited-image suffix** — `final-edit` is not an approved edit code. Use `r1` (retouched), `c1` (cropped), `bg1` (background removed), or `rs1` (resized). | `ajeets-robots_pet-bowl_detail_01_20260720-r1.jpg` |
| 6 | `ajeets-robots_canvas-wall-art_classic_detail_01_20260720.jpg` | **Unnormalized product slug + invented shot type** — two problems: (1) `canvas-wall-art-classic` includes the banned word "Classic" in the product slug (per `product-naming-standard.md`), (2) even if "classic" were meant as a shot type, `classic` is not an approved shot type — use `hero`, `detail`, `lifestyle`, `flat`, `scale`, `packaging`, or `variant`. | `ajeets-robots_canvas-wall-art_detail_01_20260720.jpg` |

**Summary of what went wrong:**

| # | Failed rules |
|---|-------------|
| 1 | Capitalization — Title Case + uppercase extension |
| 2 | Special characters — apostrophe in product slug |
| 3 | Spaces — spaces in product slug, around underscores, unpadded sequence |
| 4 | Version numbers — `v2` in place of sequence number |
| 5 | Edited-image suffix — freeform `final-edit` instead of approved edit code |
| 6 | Special characters + shot type — unnormalized "Classic" in product slug, invented shot type |

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
| No special characters except `-` `_` `.` | `womens-sneakers_hero_01_20260720.jpg` | `women's-sneakers_hero_01_20260720.jpg` |
| No version numbers in base filename | `tumbler_hero_02_20260720.jpg` | `tumbler_hero_v2_01_20260720.jpg` |
| Edited images use approved suffix codes only | `…_20260720-r1.jpg`, `…_20260720-bg1-rs1.jpg` | `…_20260720_final.jpg`, `…_20260720-edit.jpg` |
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

### Edited derivatives

```
# Original (no suffix — source of truth)
ajeets-robots_notebook_hero_01_20260720.jpg

# Retouched/color-corrected
ajeets-robots_notebook_hero_01_20260720-r1.jpg

# Retouched, then cropped
ajeets-robots_notebook_hero_01_20260720-r1-c1.jpg

# Background removed + web-optimized
ajeets-robots_pet-bowl_hero_01_20260720-bg1-rs1.jpg
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
| 1.1 | 2026-07-20 | Added dedicated **Filename Component Rules** section covering spaces, capitalization, special characters (with full character ban list + transliteration table), version numbers, and edited-image suffixes. Added **12 correct filename examples** from the 6 Printify products in the Photo Asset Plan (Canvas Wall Art, Tumbler, Backpack, Notebook, Pet Bowl, Women's Sneakers). Added **6 incorrect filename examples** with specific failure analysis (capitalization, special characters/apostrophes, spaces, version numbers in wrong place, freeform edit suffixes, unnormalized product slug + invented shot type). |
| 1.0 | 2026-07-20 | Initial standard. Format: `<brand>_<product>_<shot-type>_<sequence>_<date>.<ext>`. Defined 7 approved shot types (hero, detail, lifestyle, flat, scale, packaging, variant). Aligned product slug normalization with `product-naming-standard.md`. |
