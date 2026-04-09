# Technical Context

## Project nature

This is a **proposal-writing repository**, not a code project. The primary artifacts are LaTeX documents, BibTeX bibliographies, compiled PDFs, and the memory-bank/construction workflow that governs how they are written. There is no application code, no test suite, and no runtime. "Building" means compiling a PDF; "testing" means `grep`-based traceability audits and structural checks.

## LaTeX toolchain

- **TeX distribution**: TeX Live 2025
- **Compiler**: `pdflatex` at `/Library/TeX/texbin/pdflatex`
- **Bibliography processor**: `bibtex` (style: `abbrv`)
- **Document class**: `files/proposalnsf.cls` — a custom NSF-style proposal class living at the repo root. The class is referenced as `\documentclass{files/proposalnsf}` from inside each abstract's/proposal's `main.tex`, with the path resolved **relative to the repo root, not the folder containing main.tex**.
- **Shared macros**: `files/code_world.tex` defines `\problem{}`, `\todo{}`, `\proposalEleven`, `\proposalEighteen`, `\proposalNineteen`, `\ie`, `\eg`, `\etal`. Imported via `\input{files/code_world}`.

### Canonical build command (run from repo root)

```sh
# For the 18E full proposal:
rm -rf proposal_18E/build && mkdir -p proposal_18E/build
pdflatex -interaction=nonstopmode -output-directory=proposal_18E/build proposal_18E/main.tex
bibtex proposal_18E/build/main
pdflatex -interaction=nonstopmode -output-directory=proposal_18E/build proposal_18E/main.tex
pdflatex -interaction=nonstopmode -output-directory=proposal_18E/build proposal_18E/main.tex
```

Four passes are needed so that `\cite{}`, `\ref{}`, and the bibliography all resolve. The `BIBINPUTS` environment variable is **not** required — bibtex finds the `.bib` file via the path in `main.aux`.

### Do not use the per-folder Makefiles

Both `abstract_18E/Makefile` and `proposal_18E/Makefile` assume the current working directory is the folder itself, but the LaTeX paths are repo-root-relative. The Makefiles do not work as written; use the canonical build command above.

### Build output is gitignored

`proposal_18E/build/` is in `.gitignore`. Only source files (`.tex`, `.bib`, `.png`) and the frozen `main18E-submitted.pdf` (in `abstract_18E/`) are tracked.

## Key dependencies

### Document infrastructure
- `files/proposalnsf.cls` — custom NSF proposal class (pre-existing, treat as vendored)
- `files/code_world.tex` — shared macros used across all focus-area LaTeX files
- `files/DE-FOA-0003612 (2).pdf` — the CFP document (authoritative source of all requirements)
- `files/review_criteria.md` — the 5 DOE merit criteria in descending weight order

### Reference materials
- `files/djjay-qualifier.pdf` — full PA-AKG research proposal (Cusati qualifying paper) — source of the three-gap analysis and E1–E4 evaluation framework
- `files/full-proposal-plan-18E.md` — v1 plan listing all six reviewer concerns with action items (source material for v2)
- `docs/18e-doe-codes.md` — Sandia-anchored Kokkos/Trilinos/LAMMPS rationale for the 18E Data Sources section

### BibTeX files
- `proposal_18E/references.bib` (330+ lines) — the **authoritative** bib for 18E, containing all PA-AKG citations
- `abstract_18E/references.bib` (334 lines) — source for the above, has known duplicate entries that were cleaned up in `proposal_18E/`
- `references.bib` at repo root (137 lines) — smaller, stale; not currently used

## Repository structure

```
doe-genesis-cfp-2026/
├── CLAUDE.md                    # Project overview and deadlines (Claude Code entry point)
├── .gitignore                   # Excludes LaTeX build artifacts and proposal_18E/build/
├── .claude/
│   ├── agents/                  # Custom agents (construction-lead, feature-architect, knowledge-steward)
│   └── skills/                  # Constellize skill workflows (specify, implement, verify, memory:*)
├── abstract_11C/                # Frozen pre-proposal — focus area 11C (submitted 2026-03-27)
├── abstract_18E/                # Frozen pre-proposal — focus area 18E (submitted 2026-03-27, ranked #1/2)
├── abstract_19B/                # Frozen pre-proposal — focus area 19B (submitted 2026-03-27)
├── proposal_18E/                # ACTIVE full-proposal workspace (v2, created 2026-04-09)
│   ├── main.tex
│   ├── abstract.tex             # (copied from abstract_18E/, unchanged)
│   ├── cover_sheet.tex
│   ├── milestones.tex           # Split file for RF-4 milestone table
│   ├── data_sources.tex         # Split file for RF-5b Data Sources
│   ├── decision_gate.tex        # Split file for RF-5a Decision Gate Metrics
│   ├── references.bib
│   ├── images/
│   └── build/                   # gitignored
├── construction/                # Design-first workspace
│   ├── design/
│   ├── requirements/            # Feature specs (v2 spec lives here)
│   └── sprints/
├── docs/                        # GitHub Pages site (public stakeholder dashboard)
│   ├── index.html
│   └── 18e-doe-codes.md
├── llm/                         # Canonical memory-bank (this tree)
│   ├── memory_bank/
│   └── features/
├── memory-bank/                 # Legacy memory-bank (parallel to llm/memory_bank, see activeContext.md)
├── files/                       # Reference materials (CFP doc, review criteria, plans, macros, class file)
└── archive/                     # Historical / superseded artifacts
```

## Infrastructure and deployment

- **Repository**: `chbrown13/doe-genesis-cfp-2026` on GitHub
- **Default branch**: `main`
- **Workflow**: feature branches + PRs (example: PR #4 for 18E v2 LaTeX work; PR #5 for memory-bank update)
- **GitHub Pages**: served from `docs/` as a stakeholder-facing dashboard. The `docs/index.html` file is the live page; update it to add links to new artifacts (compiled PDFs, planning notes).
- **No CI/CD**: no GitHub Actions, no automated compile or test runs. All verification happens in interactive sessions.

## Prior work foundation (load-bearing for the proposal narrative)

- **Brown & Cusati, ESEM 2025** — "Exploring the Evidence-Based SE Beliefs of Generative AI Tools". Bib key: `brown2025esem`. Empirically demonstrates that AI tools propagate evidence inconsistently, motivating architectural provenance enforcement.
- **Cusati & Brown, ICSE-FoSE 2026** — "From Papers to Progress: Rethinking Knowledge Accumulation in Software Engineering". Bib key: `cusati2026fose`. Direct PA-AKG precursor.
- **Edge et al. 2024** — "From Local to Global: A Graph RAG Approach to Query-Focused Summarization". Bib key: `Edge2024GraphRAG`. Seed paper for the Phase 1 small-seed calibration study (AC-5b) and the snowball starting point.
- **Cusati qualifying paper** (`files/djjay-qualifier.pdf`) — full PA-AKG research proposal with the three-gap analysis and E1–E4 evaluation axes.

## Constraints

- Pre-proposal body: 1 page max (excluding references) — submitted
- Full proposal body: **5 pages max plus references** (currently 6 pages — 1 page over, page-budget session 2026-04-10)
- Project duration: 1 year starting 2026-07-01
- Must align with DOE Genesis Mission and Executive Order 14363
- Traceability: every reviewer-driven LaTeX edit must carry `% [RF-<n>]` inline comment, grep-auditable

---

**Last updated:** 2026-04-09
