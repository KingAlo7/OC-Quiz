# Feature: IChO Kernreaktionen

## Status
implemented

## Why this exists
IChO organic tasks repeatedly use compact reaction recognition: synthesis planning, stereochemical outcomes, protecting groups, spectroscopy-linked transformations, and catalysis cycles. A dedicated category makes these high-yield transformations easy to review without mixing them into every base chapter.

## What it does
Adds a `IChO Kernreaktionen` category to `data/reactions.json`. The category is intentionally dense:

- 105 mirrored entries from the existing OC reference, because those reactions are reasonable assumed knowledge for IChO synthesis and mechanism tasks.
- 46 extra advanced entries focused on the 2026 preparatory-topic signals and recurring modern IChO motifs:
  - transition-metal elementary steps,
  - Suzuki/Sonogashira/Heck/Stille/Negishi/Kumada/Hiyama and related coupling logic,
  - C-N/C-O coupling,
  - photoredox SET, HAT/XAT, radical additions, and selected photochemical reactions,
  - carbohydrate glycoside/protecting-group chemistry,
  - peptide coupling and orthogonal protection.

## Boundaries & edge cases
- Do not include one-off host-country curiosities that only matter when explicitly announced in a preparatory problem.
- Keep entries as study references, not full university-level mechanism chapters.
- Prefer general transformations over named variants with narrow substrate scope.
- 2026-special entries are marked with `IChO 2026` and `Advanced prep` tags.
- The mirrored entries use `source_category` so the original chapter remains traceable.

## Testing & verification
- `data/reactions.json` must parse as JSON.
- Reaction IDs must be unique.
- Existing required fields `id`, `category`, and `name` must be present.
- The expected `IChO Kernreaktionen` count is 151 after running `node tools/add-icho-core-reactions.js`.

## Decision log
| Date | Decision | Why | Who |
|------|----------|-----|-----|
| 2026-06-05 | Use `category` as the folder equivalent. | The existing UI groups sidebar entries by `category` and does not have a separate folder schema. | Codex |
| 2026-06-05 | Mirror the full base reaction bank into the IChO category, then append marked 2026-special entries. | IChO assumed knowledge is broader than a short named-reaction list, and the user needs a dense training folder rather than a curated teaser. | Codex |
