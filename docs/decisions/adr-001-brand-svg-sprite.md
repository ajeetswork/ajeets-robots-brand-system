# ADR 001 — Brand Asset Delivery: Generated SVG Sprite

**Status:** Accepted
**Date:** 2026-10-08
**Repository:** `ajeetswork/ajeets-robots-brand-system`

## Question
How should consumers get shared SVG assets — package dependency vs generated sprite vs copying files?

## Decision
Generate and publish the SVG sprite from the brand-system repository, with duplicate symbol names failing the build. Consumers should reference stable symbol IDs instead of taking a runtime icon dependency or maintaining copied SVGs.

## Alternatives Considered
1. **Add a runtime icon package and reference icons by package name** — cleaner than copies but forces a JS dependency.
2. **Export a generated SVG sprite and have consumers use stable symbol IDs** — *chosen*; keeps source centralized.
3. **Copy individual SVG files into every consuming repository** — easy initially per consumer.

## Rationale (verified evidence only)
- Generated sprite keeps the source centralized and gives consumers stable symbol IDs. _(Slack #ajeets-design-review `1791460954.091039` + Drive)_
- Updates are reviewable in one repository. _(Drive Constraints)_
- The tradeoff is a small build/publish step when source SVGs change — accepted. _(Slack same message)_

## Why Rejected Alternatives Were Not Chosen
- **Copying SVGs into each app** — rejected: loses a single update path; drift becomes hard to see. _(Slack `1791460952.368169`; Drive: "Copying individual files would be simpler per consumer but makes drift likely")_
- **Runtime icon package** — rejected: forces a JavaScript runtime dependency just to render shared marks. _(Slack same message; Drive Constraint)_

## Constraints
- Consumers should not need a JavaScript runtime dependency just to render the shared marks.
- Asset names need to stay stable across web surfaces.
- Team wants updates to be reviewable in one repository.

## Consequences
- Adds a small build/publish step when source SVGs change; consumers must update the published asset when symbols change.
- Build generates one sprite file from the source SVG directory and fails when duplicate symbol names are introduced.
- Avoids drift at the cost of the build step.

## Sources
- Slack thread #ajeets-design-review `1791460874.574639` + closing `1791460956.686239` — https://ajeets.slack.com/archives/C0BGKDYVA5U/p1791460874574639?thread_ts=1791460874.574639&cid=C0BGKDYVA5U
- Design doc: *Ajeet's Robots Brand Asset Delivery Notes* — https://docs.google.com/document/d/1BUBXFr4soKCZX8Y7qUDLFRWsazlLC08MHFnB9-CpKUQ/edit (1022 chars, modified 2026-10-08T11:59:27Z)
- Evidence review: https://docs.google.com/document/d/1rijfuBAZ2tpLhxLGhrX_BprzhJLDWVYzrqwS3yMbRJ4/edit §2
- Notion: Technical Decision Register — Brand row — https://app.notion.com/p/Brand-SVG-delivery-generated-sprite-vs-package-vs-copy-3f3c1db3c3be8142a71fc4d133a29190
