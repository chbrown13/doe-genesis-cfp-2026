# Progress

**Last updated:** 2026-04-09

## Phase overview

| # | Phase | Status | Start | End |
|---|-------|--------|-------|-----|
| 0 | Project Initialization | ✅ Complete | 2026-03-05 | 2026-03-05 |
| 1 | Research Topic & Design (PA-AKG) | ✅ Complete | 2026-03-05 | 2026-03-26 |
| 2 | Pre-Proposal Submissions (11C / 18E / 19B) | ✅ Complete | 2026-03-26 | 2026-03-27 |
| 3 | 18E Full Proposal Development | 🔄 **Active** | 2026-04-01 | 2026-04-28 (due) |
| 4 | Post-Submission / Award Decision | ⏸ Pending | 2026-04-28 | ~2026-06 |
| 5 | Project Execution (if funded) | ⏸ Pending | 2026-07-01 | 2027-06-30 |

## What is built and working today

### Phase 0: Project Initialization
- [x] Project directory structure established
- [x] Memory-bank documentation system (originally at `memory-bank/`, re-established at `llm/memory_bank/` on 2026-04-09)
- [x] `.claude/agents/` configured (proposal-agent, memory-agent, construction-lead, feature-architect, knowledge-steward)
- [x] `.claude/skills/` populated with constellize workflows (specify / implement / verify / memory:*)
- [x] `CLAUDE.md` with CFP details and deadlines

### Phase 1: Research Topic & Design
- [x] PA-AKG three-layer architecture defined (knowledge representation, automation & extraction, agentic orchestration)
- [x] Three-gap analysis formalized (architectural capability, evaluation, provenance/faithfulness)
- [x] E1–E4 evaluation framework defined (span alignment, canonicalization consistency, traceability completeness, longitudinal stability)
- [x] Focus-area framings created for 11C, 18E, 19B
- [x] Prior work foundation cited (`cusati2026fose`, `brown2025esem`, Cusati qualifying paper)

### Phase 2: Pre-Proposal Submissions
- [x] 2026-03-27 — Submitted 1-page pre-proposal abstracts for 11C, 18E, 19B
- [x] 2026-03 — Internal review pass; **18E ranked #1 of 2 by all three reviewers**; six reviewer concerns captured in `files/full-proposal-plan-18E.md`
- [x] 18E invited to full proposal

### Phase 3: 18E Full Proposal (active)

**Completed in this phase:**
- [x] 2026-04-09 — Specified v2 feature `llm/features/18E-proposal-incorporate-reviewer-feedback-v2.md` (11 acceptance criteria, dual-persona adversarial review applied) — originally authored at `construction/requirements/` and moved to `llm/features/` during the memory re-establishment
- [x] 2026-04-09 — Cloned `abstract_18E/` → `proposal_18E/`; 7 unblocked RF edits applied; 4-pass `pdflatex + bibtex` compile clean (10-page PDF, 6-page body, 1 over)
- [x] 2026-04-09 — Created split files: `milestones.tex`, `data_sources.tex`, `decision_gate.tex`
- [x] 2026-04-09 — Traceability tags present for `RF-1, RF-3, RF-4, RF-5a, RF-5a-b, RF-5a-c, RF-5c`; visible `\todo{}` placeholders for `RF-2` and `RF-5b` Plan A pending Sandia meeting
- [x] 2026-04-09 — 4-gate verification pass (test integrity / health / deployment / maintainability) on the 7 unblocked ACs; clean rebuild reproducible
- [x] 2026-04-09 — 2 unused labels cleaned up during Gate 4 (`sec:milestones`, `sec:data-sources`)
- [x] 2026-04-09 — Fixed latent bug in cloned `cover_sheet.tex`: `\proposalEleven` → `\proposalEighteen`
- [x] 2026-04-09 — Removed 2 duplicate BibTeX entries (`brown2025esem`, `cusati2026fose`) that blocked the compile
- [x] 2026-04-09 — Committed `feature/18E-proposal-v2` (commit `bb506f0`) → **PR #4 merged** by Chris Brown at 20:39 UTC (merge commit `c50176e`)
- [x] 2026-04-09 — Full sync of legacy `memory-bank/` → PR #5 open on branch `feature/memory-bank-update-2026-04-09`
- [x] 2026-04-09 — Re-established `llm/memory_bank/` on canonical path per skill template (this file)

## What remains to be built

### Phase 3 blockers (external events)
- [ ] **2026-04-09 14:00** — Sandia meeting: resolve RF-2 industry partner + RF-5b Sandia corpus specifics
- [ ] **2026-04-10** — Page-budget session: bring body narrative under 5 pages (AC-8)
- [ ] **2026-04-11 EOD** — Brown triggers Plan A/B for any unresolved items

### Phase 3 downstream (before submission)
- [ ] Patch `main.tex:152` (RF-2) and `data_sources.tex:16` (RF-5b) placeholders based on Sandia meeting outcomes
- [ ] Brown + Wang joint sign-off on all 11 ACs via Cusati proxy (Sign-Off Checklist in v2 spec)
- [ ] Dry-run reviewer pass (date TBD, open question #7 in spec)
- [ ] Decide whether to remove `\input{proposal_18E/abstract}` from `main.tex` (may resolve page overrun)
- [ ] Decide whether to restore Phase 1 pilot-study interviews (open question #11 in spec)
- [ ] Merge PR #5 (legacy memory-bank sync) — not strictly required but keeps `memory-bank/` current during transition
- [ ] Create and merge the PR for `llm/memory_bank/` establishment (this branch)
- [ ] Decide disposition of legacy `memory-bank/` folder (delete, alias, or keep in parallel)
- [ ] **2026-04-28** — Full proposal submission to DOE Genesis portal
- [ ] Publish final PDF to `docs/` and link from `index.html`

### Phase 4: Post-Submission
- [ ] ~2026-06 — DOE Genesis award decision
- [ ] Respond to any post-submission clarification requests

### Phase 5: Project Execution (contingent on award)
- [ ] 2026-07-01 — Projects begin (1-year duration)
- [ ] Execute per the Methods section of the full proposal: KG schema → initial population → Phase 1 calibration → extraction pipeline → Phase 2 calibration → Month-6 Decision Gate → full evaluation → open-source release → dissemination

## Known bugs / tech debt (non-blocking, inherited from pre-proposal artifacts)

- **Pre-existing bibtex warnings**: `krofcheck2023overview` and `Park2023GenerativeAgents` have empty `journal` fields in `abstract_18E/references.bib` and (carried over to) `proposal_18E/references.bib`. Non-fatal, bibtex still compiles, but the rendered citations will have blank journals.
- **Multiply-defined label**: `abstract_18E/cover_sheet.tex` and `proposal_18E/cover_sheet.tex` both use `\label{tab:my_label}` twice (once for the personnel table, once for the budget table). Produces a LaTeX warning but no visible effect since no `\ref{tab:my_label}` is used.
- **Stale Makefiles**: both `abstract_18E/Makefile` and `proposal_18E/Makefile` assume CWD = folder, but the LaTeX paths are repo-root-relative. The Makefiles do not work as written. Use the canonical build command in `techContext.md` instead.
- **`\problem{}` macro arity**: the macro in `files/code_world.tex:23` is defined as `\newcommand{\problem}[2]{...}` (2 mandatory args) but called with 1 argument at `main.tex:70`. The submitted PDF renders correctly despite this (empirically verified), but it is a latent oddity.
- **`docs/index.html` stale links**: the three pre-proposal download cards point to `./abstract1.pdf`, `./abstract2.pdf`, `./abstract3.pdf` which don't exist at those paths (the submitted PDFs are in `abstract_18E/main18E-submitted.pdf` etc.). Not blocking since no one is actively using those links.

## Key milestones reached

| Date | Milestone |
|---|---|
| 2026-03-05 | Project initialized, memory-bank and construction workspace created |
| 2026-03-27 | Pre-proposal abstracts submitted for 11C, 18E, 19B |
| ~2026-03 | Internal review complete; 18E ranked #1/2; invited to full proposal |
| 2026-04-09 | v2 reviewer-feedback incorporation: spec → implement → verify → PR #4 merged |
| 2026-04-09 | Memory-bank re-established at canonical `llm/memory_bank/` path |

## Deadlines ahead

| Date | Event |
|---|---|
| 2026-04-09 14:00 | Sandia meeting — resolves RF-2, RF-5b Plan A |
| 2026-04-10 | Page-budget session — resolves AC-8 |
| 2026-04-11 EOD | Brown triggers Plan A/B |
| **2026-04-28** | **Full proposal submission deadline** |
| ~2026-06 | DOE Genesis award decision |
| 2026-07-01 | Project start (if funded) |
| 2027-06-30 | Project end (1 year) |
