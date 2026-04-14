# Feature Specs

This directory holds feature specifications produced by the constellize skill workflow:

- **`/constellize:feature:specify <name>`** — writes a new spec here with status `SPECIFIED`
- **`/constellize:feature:implement`** — reads a `SPECIFIED` spec, applies edits, sets status to `PARTIALLY IMPLEMENTED` or `IMPLEMENTED`
- **`/constellize:feature:verify`** — reads an `IMPLEMENTED` spec, runs 4 quality gates, sets status to `PARTIALLY VERIFIED` or `VERIFIED`

## Historical note

Before the canonical `llm/` tree was established on 2026-04-09, feature specs lived at `construction/requirements/<name>.md`. The first spec produced that way — `18E-proposal-incorporate-reviewer-feedback-v2.md` — was moved here via `git mv` as part of the same establishment work:

- `llm/features/18E-proposal-incorporate-reviewer-feedback-v2.md` — 18E reviewer-feedback incorporation, status `PARTIALLY VERIFIED` as of 2026-04-09. Authoritative spec for the 18E full-proposal work.

The `construction/requirements/` directory still holds non-feature-style checklists (e.g., `abstract-polish-workflow.md`) and the `spec_builder.md` template.

## File naming

- Use kebab-case: `<topic>-<feature-description>-v<N>.md`
- Example: `18E-proposal-incorporate-reviewer-feedback-v2.md`
