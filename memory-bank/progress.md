# Progress


### Phase 0: Project Initialization and Pre-Proposal
- [x] Created project directory structure
- [x] Set up memory-bank documentation system
- [x] Configured .claude/agents (proposal-agent, memory-agent)
- [x] Created CLAUDE.md with CFP details and deadlines
- [x] Analyzed CFP document and captured requirements

### Phase 2: Pre-Proposal Submissions (complete)
- [x] 2026-03-27 — Submitted 1-page pre-proposal abstracts for 11C, 18E, 19B (all three focus areas)
- [x] 2026-03 — All three reviewed internally; 18E ranked **#1 of 2** by all three reviewers; six reviewer concerns captured as RF-1..RF-6 in `files/full-proposal-plan-18E.md`

### Phase 3: 18E Full Proposal (in progress, due 2026-04-28)

**Completed:**
- [x] 2026-04-09 — Specified v2 feature `18E-proposal-incorporate-reviewer-feedback-v2.md` (11 acceptance criteria, dual-persona review applied)
- [x] 2026-04-09 — Cloned `abstract_18E/` → `proposal_18E/`; 7 unblocked RF edits applied; 4-pass pdflatex+bibtex compile clean (10-page PDF, 6-page body — 1 page over, deferred to Friday)
- [x] 2026-04-09 — Created split files: `milestones.tex`, `data_sources.tex`, `decision_gate.tex`
- [x] 2026-04-09 — Traceability tags `[RF-1, RF-3, RF-4, RF-5a, RF-5a-b, RF-5a-c, RF-5c]` present; visible placeholders for RF-2 and RF-5b Plan A pending Sandia meeting
- [x] 2026-04-09 — 4-gate verification pass (test integrity / health / deployment / maintainability) on the 7 unblocked ACs; clean rebuild reproducible; 2 unused labels cleaned up during Gate 4
- [x] 2026-04-09 — Committed and pushed feature branch `feature/18E-proposal-v2`; opened PR #4 (https://github.com/chbrown13/doe-genesis-cfp-2026/pull/4)
- [x] 2026-04-09 — **PR #4 merged** by Chris Brown (merge commit `c50176e`); `main` now contains the v2 work
- [x] 2026-04-09 — Full memory-bank update applied on a separate branch `feature/memory-bank-update-2026-04-09`

**Blocked on external events:**
- [ ] 2026-04-09 14:00 — Sandia meeting: resolve RF-2 industry partner + RF-5b Sandia corpus specifics
- [ ] 2026-04-10 — Page-budget session: bring body narrative under 5 pages (AC-8)
- [ ] 2026-04-11 EOD — Brown triggers Plan A/B for any unresolved items

**Downstream before submission:**
- [ ] Patch `main.tex:152` (RF-2) and `data_sources.tex:16` (RF-5b) placeholders based on Sandia meeting outcomes
- [ ] Brown + Wang joint sign-off on all 11 ACs via Cusati proxy (Sign-Off Checklist in v2 spec)
- [ ] Dry-run reviewer pass (date TBD, open question #7 in spec)
- [ ] Decide whether to remove `\input{proposal_18E/abstract}` from `main.tex` (may solve page overrun)
- [ ] Decide whether to restore Phase 1 pilot-study interviews (open question #11 in spec)
- [x] Merge PR #4 (merged 2026-04-09 by Chris Brown, merge commit `c50176e`)
- [ ] 2026-04-28 — Full proposal submission deadline
- [ ] Publish final PDF to `docs/` (link from `index.html`)

### Phase 4: Post-Submission (2026-06 onwards)
- [ ] ~June 2026 — Genesis acceptance notification
- [ ] 2026-07-01 — Projects begin (1-year duration)

### Known hygiene debt (inherited from pre-proposal artifacts, non-blocking)
- `abstract_18E/references.bib` has pre-existing bibtex warnings (`krofcheck2023overview`, `Park2023GenerativeAgents` have empty `journal` fields)
- `abstract_18E/cover_sheet.tex` has `\label{tab:my_label}` used twice (multiply-defined warning)
- The in-folder `Makefile`s in both `abstract_18E/` and `proposal_18E/` assume CWD = folder but the LaTeX paths are repo-root-relative — the Makefiles do not work as written
- The `\problem{}` macro in `files/code_world.tex` is defined with 2 mandatory args but called with 1 at `main.tex:70` (renders correctly empirically but is a latent oddity)

**Note:** Update after every task completion. Last full sync: 2026-04-09.
