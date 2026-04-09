# Active Context

**Last updated:** 2026-04-09 (full memory-bank sync after v2 implementation + verification + PR #4 merge)

## Current Work Focus

**18E full proposal (v2)** — incorporating the six reviewer concerns from the submitted pre-proposal review round into `proposal_18E/main.tex` (new folder, parallel to the frozen `abstract_18E/`). The v2 spec at `construction/requirements/18E-proposal-incorporate-reviewer-feedback-v2.md` is the contract; 7 of 11 acceptance criteria are materially satisfied and verified, 2 are blocked on today's 14:00 Sandia meeting, and 1 (page count) is deferred to tomorrow's page-budget session.

## Recent Changes (2026-04-09)

- Ran full constellize skill chain: `/specify` → `/implement` → `/verify` on the 18E v2 feature.
- Created `proposal_18E/` as a cloned-and-edited copy of `abstract_18E/` so the two versions can be compared directly (user requested this explicitly; v1 = the plan doc, not a LaTeX version).
- Introduced the **inline `[RF-<n>]` traceability pattern** as the canonical mechanism for connecting reviewer feedback to LaTeX edits. Every RF edit now carries an inline comment tag and is grep-auditable. Documented in `systemPatterns.md`.
- Reframed AC-5 (Decision Gate Metrics) from first-pass numeric commitments (≥80% provenance completeness, etc.) to **scaling-behavior claims with empirically-discovered thresholds** via a two-phase calibration study (AC-5b small seed ~5–10 papers, AC-5c expanded snowball ~50+). The Phase 1 → Phase 2 threshold progression *is* the AI advantage evidence the CFP asks for.
- Established the **sign-off proxy pattern**: Brown + Wang are the joint sign-off authority; Cusati proxies by relaying decisions into the spec's Sign-Off Checklist.
- Established the **Plan A / Plan B branching pattern**: Brown is the named triggerer for RF-2 and RF-5b Plan A/B by 2026-04-11 EOD if the Sandia meeting doesn't resolve them cleanly.
- Committed the work as `feature/18E-proposal-v2` (commit `bb506f0`, 37 files, +4336 LOC) and opened PR **chbrown13/doe-genesis-cfp-2026#4**.
- **PR #4 merged** by Chris Brown on 2026-04-09 at 20:39 UTC (merge commit `c50176e`). `main` now contains the v2 work; local `main` advanced to origin/main via fast-forward.
- Applied `full` memory-bank sync on a separate branch `feature/memory-bank-update-2026-04-09` — keeping memory-bank changes logically distinct from the LaTeX work now on `main`.

## Immediate Next Steps (chronological)

1. **Today 14:00 — Sandia meeting.** Bring back answers on (a) industry partner commitment or candidate engagement, and (b) specific Sandia corpus subsets (Kokkos / Trilinos / LAMMPS) accessible under existing data agreements. Two `\todo{}` placeholders (`main.tex:152`, `data_sources.tex:16`) are visible and ready for swap.
2. **Tomorrow 2026-04-10 — Page-budget session.** Body is currently 6 pages (1 over the 5-page limit). Quick win to evaluate: drop `\input{proposal_18E/abstract}` from `main.tex` line 27, which removes the pre-proposal abstract from the full-proposal PDF and may resolve the overrun without prose cuts. Open question whether the abstract belongs in the compiled full-proposal PDF at all.
3. **2026-04-11 EOD — Brown triggers Plan A/B** for any item still unresolved from the Sandia meeting. Cusati proxies the decision into the spec Amendment Log.
4. **Through 2026-04-28** — Brown + Wang joint sign-off on all 11 ACs (via Cusati proxy); any sign-off staleness handled via the material-change rule.
5. **2026-04-28** — Full proposal submission.

## Known Open Questions (from the v2 spec)

1. **AC-8 escalation** if Friday's cuts don't hit 5 pages — team discussion, not pre-committed.
2. **Final PDF distribution location** — default `docs/` + link from `index.html`.
3. **Dry-run reviewer pass** — date and reviewer TBD.
4. **Plan B candidate partner naming** — HPE/NVIDIA/AWS specifically, or stay generic?
5. **First page-budget cut candidate** — architecture figure vs. prose?
6. **Steinmetz involvement in AC-6 Plan A sign-off** — Brown + Wang are joint signers but Sandia specifics are Steinmetz's expertise.
7. **Pilot-study interviews** — dropped from Phase 1 during implementation to fit calibration study; should they be restored (Phase 1 or Phase 2)?

## What's NOT Active Right Now

- 11C and 19B full proposals — status depends on whether they're invited to full proposal; only 18E is confirmed primary. `abstract_11C/` and `abstract_19B/` remain frozen.
- Budget / Appendix 2 / computing resource requests — separate deliverables, explicitly out of scope for the v2 reviewer-feedback work.
- `docs/index.html` is live on GitHub Pages but hasn't been updated with the full-proposal PDF yet (will happen post-submission).

## Context for a Fresh Session

If you're picking this up after a break, the minimum you need to know:
1. Read `construction/requirements/18E-proposal-incorporate-reviewer-feedback-v2.md` — it's the source of truth.
2. Look at the Sign-Off Checklist at the bottom to see which ACs have signoff.
3. Look at the Amendment Log to see what's changed recently.
4. PR #4 is **merged**; the v2 work is on `main`. Subsequent reviewer-feedback cycles should create new feature branches off `main`.
5. `grep '\[RF-' proposal_18E/` audits which reviewer concerns are addressed.
6. `grep '\\todo{' proposal_18E/main.tex` should return exactly the RF-2 placeholder (1 hit) until Sandia meeting resolves; 0 at final submission.
