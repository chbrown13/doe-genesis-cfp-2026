# Active Context

**Last updated:** 2026-04-09

## Current work focus

**18E full proposal (v2)** — incorporating the six reviewer concerns from the 18E pre-proposal review round into `proposal_18E/main.tex` (new folder, parallel to the frozen `abstract_18E/`). The construction spec at `llm/features/18E-proposal-incorporate-reviewer-feedback-v2.md` is the contract; 7 of 11 acceptance criteria are materially satisfied and verified, 2 are blocked on today's 14:00 Sandia meeting, and 1 (page count) is deferred to tomorrow's page-budget session.

PR #4 (the v2 LaTeX work) was merged to `main` earlier today. PR #5 (the legacy `memory-bank/` full sync) is currently open. This file is being created as part of **`llm/memory_bank/` establishment** — a canonical-path re-establishment of the memory bank per the constellize skill template.

## Recent changes (2026-04-09)

- Ran the full constellize skill chain: `/specify` → `/implement` → `/verify` on the 18E v2 feature.
- Created `proposal_18E/` as a cloned-and-edited copy of `abstract_18E/` so both versions can be compared directly.
- Introduced the **inline `[RF-<n>]` traceability pattern** as the canonical mechanism for connecting reviewer feedback to LaTeX edits (see `systemPatterns.md`).
- Reframed AC-5 (Decision Gate Metrics) from first-pass numeric commitments to **scaling-behavior claims with empirically-discovered thresholds** via a two-phase calibration study (AC-5b small seed ~5–10 papers, AC-5c expanded snowball ~50+). The Phase 1 → Phase 2 threshold progression constitutes the direct AI advantage evidence the CFP asks for.
- Established the **sign-off proxy pattern**: Brown + Wang are joint sign-off authority; Cusati proxies decisions into the spec's Sign-Off Checklist with a material-change staleness rule.
- Established the **Plan A / Plan B branching pattern**: Brown is the named triggerer for RF-2 and RF-5b Plan A/B by 2026-04-11 EOD.
- Committed `feature/18E-proposal-v2` (commit `bb506f0`, 37 files, +4336 LOC) → **PR #4 merged** by Chris Brown at 2026-04-09 20:39 UTC (merge commit `c50176e`).
- Synced the legacy `memory-bank/` on branch `feature/memory-bank-update-2026-04-09` → **PR #5 open**.
- Re-established the canonical `llm/memory_bank/` tree per the skill's template on branch `feature/establish-llm-memory-bank` — that's what you're reading now.

## Immediate next steps (chronological)

1. **Today 14:00 — Sandia meeting.** Bring back answers on (a) industry partner commitment or candidate engagement, and (b) specific Sandia corpus subsets (Kokkos / Trilinos / LAMMPS) accessible under existing data agreements. Two `\todo{}` placeholders (`main.tex:152`, `data_sources.tex:16`) are visible and ready for swap.
2. **Tomorrow 2026-04-10 — Page-budget session.** Body is currently 6 pages (1 over the 5-page limit). Quick win to evaluate: drop `\input{proposal_18E/abstract}` from `main.tex` line 27, which removes the pre-proposal abstract from the full-proposal PDF and may resolve the overrun without prose cuts.
3. **2026-04-11 EOD — Brown triggers Plan A/B** for any item still unresolved from the Sandia meeting. Cusati proxies the decision into the spec Amendment Log.
4. **Through 2026-04-28** — Brown + Wang joint sign-off on all 11 ACs (via Cusati proxy); any sign-off staleness handled via the material-change rule.
5. **2026-04-28** — Full proposal submission.

## Open decisions / unresolved questions

These are copied from `llm/features/18E-proposal-incorporate-reviewer-feedback-v2.md` Open Questions:

1. **AC-8 escalation** if Friday's cuts don't hit 5 pages — team discussion, not pre-committed.
2. **Final PDF distribution location** — default `docs/` + link from `index.html`.
3. **Dry-run reviewer pass** — date and reviewer TBD.
4. **Plan B candidate partner naming** — HPE/NVIDIA/AWS specifically, or stay generic?
5. **First page-budget cut candidate** — architecture figure vs. prose?
6. **Steinmetz involvement in AC-6 Plan A sign-off** — Brown + Wang are joint signers but Sandia specifics are Steinmetz's expertise.
7. **Pilot-study interviews** — dropped from Phase 1 during implementation to fit calibration study; should they be restored (Phase 1 or Phase 2)?
8. **Disposition of legacy `memory-bank/` folder** — **Decided 2026-04-09**: delete after PR #6 (`llm/memory_bank/` establishment) merges. Delete happens in a separate follow-up PR so it can be reviewed on its own terms. PR #5 (legacy memory-bank sync) is still open — the user may merge or close it depending on whether they want the legacy folder kept in sync before the delete.
9. ~~Disposition of the v2 spec location~~ — **Resolved 2026-04-09**: moved from `construction/requirements/` to `llm/features/18E-proposal-incorporate-reviewer-feedback-v2.md` via git rename. All references updated.

## What's NOT active right now

- **11C and 19B full proposals** — only 18E was confirmed as primary and invited to full proposal. `abstract_11C/` and `abstract_19B/` remain frozen; no active work.
- **Budget / Appendix 2 / computing resource requests** — separate deliverables, explicitly out of scope for the v2 reviewer-feedback work.
- **`docs/index.html`** — live on GitHub Pages but not updated with the final full-proposal PDF yet (will happen post-submission).
- **PA-AKG implementation** — no code written. The research execution repo is a separate project that starts 2026-07-01 if funded.

## Context for a fresh session

If you're picking this up after a break, the minimum you need to know:

1. **Source of truth for the v2 work**: `llm/features/18E-proposal-incorporate-reviewer-feedback-v2.md` — includes the Sign-Off Checklist and Amendment Log at the bottom.
2. **Current PR status**: PR #4 (18E LaTeX v2) **merged**; PR #5 (legacy memory-bank sync) **open**; PR for `llm/memory_bank/` establishment **to be created**.
3. **Traceability audit**: `grep '\[RF-' proposal_18E/` to see which reviewer concerns are addressed.
4. **`\todo{}` count on `main.tex`**: should be exactly 1 (the RF-2 placeholder) until the Sandia meeting resolves; 0 at final submission.
5. **Canonical build command**: in `techContext.md` under "Canonical build command".
6. **PA-AKG research approach**: in `projectbrief.md` under "Research problem and approach".
