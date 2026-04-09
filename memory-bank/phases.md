# Phases — Coordination Hub

## Phase Registry

| # | Phase | Status | Start | End |
|---|-------|--------|-------|-----|
| 0 | Project Initialization | Complete | 2026-03-05 | 2026-03-05 |
| 1 | Research Topic & Design (PA-AKG) | Complete | 2026-03-05 | 2026-03-26 |
| 2 | Pre-Proposal Submissions (11C / 18E / 19B) | Complete | 2026-03-26 | 2026-03-27 |
| 3 | 18E Full Proposal Development | **Active** | 2026-04-01 | 2026-04-28 (due) |
| 4 | Post-Submission / Award Decision | Pending | 2026-04-28 | ~2026-06 |
| 5 | Project Execution (if funded) | Pending | 2026-07-01 | 2027-06-30 |

## Phase Details

### Phase 0: Project Initialization (complete)
- **Objective**: Set up project infrastructure
- **Deliverables**: Memory-bank, construction folder, agent configs, CLAUDE.md
- **Status**: Complete

### Phase 1: Research Topic & Design (complete)
- **Objective**: Select research topic, define PA-AKG approach, create design documents
- **Deliverables**: PA-AKG three-layer architecture, three-gap analysis, E1–E4 evaluation framework, focus-area framings for 11C / 18E / 19B
- **Status**: Complete — PA-AKG concept finalized across all three focus areas

### Phase 2: Pre-Proposal Submissions (complete)
- **Objective**: Draft and submit 1-page pre-proposal abstracts
- **Deliverables**: Three 1-page pre-proposals (11C, 18E, 19B), bibliography, portal submission
- **Deadline**: 2026-03-27
- **Status**: Complete — all three submitted. 18E ranked #1/2 by all three internal reviewers, invited to full proposal.

### Phase 3: 18E Full Proposal Development (active)
- **Objective**: Develop the 5-page + references full proposal for focus area 18E, incorporating the six reviewer concerns raised in the Phase 2 review round
- **Deliverables**:
  - `proposal_18E/main.tex` + split files (`milestones.tex`, `data_sources.tex`, `decision_gate.tex`) — **created and partially complete (PR #4 merged 2026-04-09)**
  - Construction spec: `construction/requirements/18E-proposal-incorporate-reviewer-feedback-v2.md` — 11 acceptance criteria, 7 verified, 2 blocked, 1 deferred
  - All RF-1..RF-6 concerns materially addressed and traceable via inline `[RF-<n>]` tags
  - Compiled PDF ≤ 5 pages body + references
  - Brown + Wang joint sign-off on all 11 ACs (Cusati proxy)
- **Deadline**: 2026-04-28
- **Status**: Active. PR #4 merged. 7 unblocked ACs verified. Awaiting: 2026-04-09 Sandia meeting (RF-2, RF-5b Plan A); 2026-04-10 page-budget session (AC-8); 2026-04-11 EOD Plan A/B trigger by Brown; final Brown+Wang sign-off.

### Phase 4: Post-Submission / Award Decision (pending)
- **Objective**: Submit full proposal and await DOE Genesis award decision
- **Deliverables**: Submitted full proposal artifact; `docs/` updated with final PDF
- **Deadline**: 2026-04-28 submission; ~2026-06 decision
- **Status**: Pending

### Phase 5: Project Execution (pending, contingent on award)
- **Objective**: Execute the 1-year PA-AKG research project
- **Deliverables**: Per the Methods section of the full proposal — KG schema, initial population, Phase 1 calibration, extraction pipeline, expanded-corpus Phase 2 calibration, Month-6 Decision Gate, full evaluation, open-source release, dissemination
- **Timeline**: 2026-07-01 through 2027-06-30
- **Status**: Pending

## Document Structure

```
doe-genesis-cfp-2026/
├── CLAUDE.md                    # Project overview and deadlines
├── .claude/
│   ├── agents/                  # (legacy proposal-agent, memory-agent + constellize agents)
│   └── skills/                  # constellize:feature:* and constellize:memory:* skill workflows
├── memory-bank/                 # Living documentation
│   ├── README.md
│   ├── projectbrief.md
│   ├── productContext.md
│   ├── techContext.md
│   ├── systemPatterns.md
│   ├── activeContext.md
│   ├── progress.md
│   ├── phases.md                # (this file)
│   ├── architecturalDecisions.md
│   └── archive/
├── construction/                # Design-first workspace
│   ├── README.md
│   ├── spec_builder.md
│   ├── design/
│   ├── requirements/            # v2 spec lives here
│   └── sprints/
├── abstract_11C/                # Frozen pre-proposal (11C)
├── abstract_18E/                # Frozen pre-proposal (18E, reviewed #1/2) — DO NOT EDIT
├── abstract_19B/                # Frozen pre-proposal (19B)
├── proposal_18E/                # Active full proposal workspace (v2)
│   ├── main.tex
│   ├── abstract.tex
│   ├── cover_sheet.tex
│   ├── milestones.tex           # RF-4 split file
│   ├── data_sources.tex         # RF-5b split file
│   ├── decision_gate.tex        # RF-5a split file
│   ├── references.bib
│   └── build/                   # gitignored
├── docs/                        # GitHub Pages site
│   ├── index.html
│   └── 18e-doe-codes.md         # Sandia-anchored code rationale
└── files/                       # Reference materials
    ├── DE-FOA-0003612 (2).pdf   # CFP document
    ├── full-proposal-plan-18E.md # v1 reviewer-feedback plan
    ├── review_criteria.md
    └── Genesis pre-proposal reviews - Brown.xlsx
```

## Cross-Reference Index

| File | Purpose |
|------|---------|
| `memory-bank/projectbrief.md` | CFP requirements and success criteria |
| `memory-bank/productContext.md` | PA-AKG research approach and focus-area framings |
| `memory-bank/techContext.md` | LaTeX toolchain, bib conventions, build commands |
| `memory-bank/systemPatterns.md` | Conventions including traceability pattern, sign-off proxy, Plan A/B branching |
| `memory-bank/activeContext.md` | Current session state (updated every session) |
| `memory-bank/progress.md` | Task tracking per phase |
| `memory-bank/architecturalDecisions.md` | ADRs 001–007 |
| `construction/requirements/18E-proposal-incorporate-reviewer-feedback-v2.md` | **v2 spec — source of truth for the full proposal work** |
| `files/full-proposal-plan-18E.md` | v1 reviewer-feedback action plan (source material for v2) |
| `docs/18e-doe-codes.md` | Sandia-anchored Kokkos/Trilinos/LAMMPS rationale |

---

**Note:** Update at phase transitions. Last updated 2026-04-09.
