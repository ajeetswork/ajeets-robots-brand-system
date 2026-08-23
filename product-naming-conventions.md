# Product Naming Conventions – Ajeets Robots

Source: Live Printify catalog audit – Shop "Ajeets" (ID 27965389) – 2026-08-23
Store: https://ajeets.printify.me/

## Problem

Product titles in the live Printify store are inconsistent across branding, capitalization, punctuation, and structure. This hurts search/discovery and looks unprofessional.

### Inconsistent brand name spellings

| Printify ID | Live Title |
|-------------|------------|
| 6a51683a667e100da0023852 | Ajeet Robot mens tee |
| 6a5168cbe9a49638fb0ebfb6 | Ajeets Robot's - Polo Tee |
| 6a36ec18df35581392104fe5 | Ajeets Robots - Women's Tee |
| 6a5162e4e9a49638fb0ebc77 | AJEETS ROBOTS - Classic Mug |

Brand name appears as: `Ajeet Robot` / `Ajeets Robot's` / `Ajeets Robots` / `AJEETS ROBOTS`

### Other inconsistencies

| Issue | Examples |
|-------|----------|
| All-lowercase title | `journal` (6a51641ae9a49638fb0ebd2d) |
| Double pipe separator | `Ajeets Robots || Classic Backpack` (6a516480e4c7663cd00430fd) |
| Trailing space | `Ajeets Robots - Classic Shower Curtain ` (6a51695ee4c7663cd00433ca) |
| Inconsistent possessive | `Ajeets Robot's` vs `Ajeets Robots` |
| Missing gender marker case | `mens tee` (lowercase) vs `Women's Tee` (Title Case) |
| Numbered products | `Women's Sweatshirt #1` (6a417d363481506f0807308f) |
| Vague SEO-poor titles | `journal`, `Classic Mug` – flagged in customer complaints (see ajeets-robots-store-qa/customer-complaints-resolution-guide.md) |

## Naming Standard

**Format:** `Ajeets Robots - {Product Name}`

**Rules:**

1. **Brand prefix:** Always `Ajeets Robots` – Title Case, plural, no possessive apostrophe
2. **Separator:** Single hyphen with spaces: ` - ` – never `||`, `—`, or no separator
3. **Product name:** Title Case (e.g. `Women's Tee`, not `womens tee`)
4. **Gender/audience markers:** Title Case – `Men's`, `Women's`, `Kids`, `Unisex`
5. **No all-caps:** Never `AJEETS ROBOTS`
6. **No ALL-lowercase:** Never `journal`
7. **No trailing whitespace**
8. **No numbered series** (`#1`, `#2`) – use descriptive differentiators instead
9. **SEO keywords:** Include material/use-case when it helps discovery (e.g. `Canvas Wall Art Print` not just `Wall Art`)

## Migration Checklist

Products needing title fixes (as of 2026-08-23):

- [ ] `Ajeet Robot mens tee` (6a51683a667e100da0023852) → `Ajeets Robots - Men's Tee`
  - Also: missing marketing description, currently hidden (`visible: false`)
- [ ] `AJEETS ROBOTS - Classic Mug` (6a5162e4e9a49638fb0ebc77) → `Ajeets Robots - Classic Mug`
- [ ] `journal` (6a51641ae9a49638fb0ebd2d) → `Ajeets Robots - Classic Journal`
- [ ] `Ajeets Robots || Classic Backpack` (6a516480e4c7663cd00430fd) → `Ajeets Robots - Classic Backpack`
- [ ] `Ajeets Robot's - Polo Tee` (6a5168cbe9a49638fb0ebfb6) → `Ajeets Robots - Polo Tee`
- [ ] `Ajeets Robots - Classic Shower Curtain ` (6a51695ee4c7663cd00433ca) → trim trailing space
- [ ] `Ajeets Robots - Women's Sweatshirt #1` (6a417d363481506f0807308f) → add descriptive differentiator, remove `#1`

### Customer-complaint titles (from store-qa repo)

- [ ] `Canvas Wall Art Print` (6a36b8fbeb0b93244f0d9773) – add keywords: size, theme, style
- [ ] `2026 Wall Calendar` (6a36b87966b72a2af10e4f95) – add descriptive keywords
- [ ] `Leather Patch Hat` (6a38015588d5d893550c5d34) – description too short, expand with material/fit/care

## Related

- Catalog snapshot: `ajeets-robots-catalog/catalog-snapshot-2026-08-23.md`
- Customer complaints: `ajeets-robots-store-qa/customer-complaints-resolution-guide.md`
- Variant QA: `ajeets-robots-store-qa/variant-review-checklists.md`
