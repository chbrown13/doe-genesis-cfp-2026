# Technical Context

## Research Methodology (planned, not yet implemented)

PA-AKG will be built as an open-source reference implementation. The methodology is deliberately hybrid:

- **Symbolic layer**: property graph store (Neo4j as primary development target; Amazon Neptune as cloud deployment evaluation target) encoding typed entities and explicit semantic relations.
- **Semantic layer**: dense vector index (FAISS for local experimentation; pgvector for integrated property-graph + vector-index queries) for approximate similarity search over long-form source passages.
- **Extraction**: structured prompting against a multi-backend LLM pool (Llama 3 for local/private inference, GPT-4 and Claude as high-capability baselines, CodeLlama for code-specific tasks).
- **Provenance enforcement**: span-level alignment and canonicalization auditing are architectural constraints enforced at every agent handoff, not post-hoc reporting.
- **Agentic orchestration**: adapting the Planning & Control pattern (Park et al. 2023); four role types (ranking, continuation, evaluation, synthesis).

For the 18E full proposal, evaluation thresholds are discovered empirically via two calibration studies (see `productContext.md`), not pre-committed.

## Proposal Document Toolchain

### LaTeX stack
- **TeX distribution**: TeX Live 2025 (`pdflatex` at `/Library/TeX/texbin/pdflatex`)
- **Document class**: `files/proposalnsf.cls` (custom NSF-style proposal class, repo-root-relative import)
- **Shared macros**: `files/code_world.tex` defines `\problem{}`, `\todo{}`, `\proposalEleven`, `\proposalEighteen`, `\proposalNineteen`, `\ie`, `\eg`, `\etal`
- **Bibliography style**: `abbrv` via BibTeX
- **Compile pattern**: 4-pass `pdflatex → bibtex → pdflatex → pdflatex`, invoked **from the repo root** (paths in `main.tex` are repo-root-relative, e.g. `\input{proposal_18E/abstract}`, `\includegraphics{proposal_18E/images/...}`)
- **Stale Makefiles** exist inside both `abstract_18E/` and `proposal_18E/` but assume CWD = folder (which breaks the repo-root-relative paths). Do not use them without fixing. The canonical build command is documented in `construction/requirements/18E-proposal-incorporate-reviewer-feedback-v2.md` Amendment Log.
- **Build artifact directories** (`proposal_18E/build/`, etc.) are gitignored.

### Artifact layout
- `abstract_18E/` — **frozen** pre-proposal (submitted 2026-03-27, ranked #1/2 in reviews). Do not edit.
- `proposal_18E/` — full-proposal workspace (v2, created 2026-04-09). Parallel to `abstract_18E/` for comparison.
- `abstract_11C/`, `abstract_19B/` — frozen pre-proposals for the other two focus areas.
- Top-level `references.bib` (137 lines, smaller) is distinct from `proposal_18E/references.bib` (320+ lines, authoritative for 18E).

### Traceability convention (introduced v2, 2026-04-09)
Every reviewer-driven LaTeX edit carries an inline comment of the form:
```latex
% [RF-<n>] <short reviewer concern> — verified by: AC-<m>
```
`grep '\[RF-' proposal_18E/` audits coverage. See `systemPatterns.md` for the full pattern.

## Prior Work Foundation

- **Brown & Cusati, ESEM 2025** — evidence-based beliefs of generative AI tools (SE validation context). Bib key: `brown2025esem`.
- **Cusati & Brown, ICSE-FoSE 2026** — "From Papers to Progress: Rethinking Knowledge Accumulation in Software Engineering". Direct PA-AKG precursor. Bib key: `cusati2026fose`.
- **Qualifying paper** (`files/djjay-qualifier.pdf`) — full research proposal for PA-AKG with the E1–E4 evaluation framework and three-gap analysis.
- **Edge et al. 2024 Graph-Based RAG** — seed paper for the Phase 1 small-seed calibration study (AC-5b). Bib key: `Edge2024GraphRAG`.

## Project Infrastructure

- **Repository**: `chbrown13/doe-genesis-cfp-2026` on GitHub
- **Default branch**: `main`
- **Workflow**: feature branches + PRs (see `.github/` — PR #4 created 2026-04-09 for the 18E v2 work)
- **Documentation**: memory-bank/ (this folder) + construction/ (design-first workspace) + docs/ (GitHub Pages)
- **Claude skills**: `.claude/skills/constellize:*` provide specify / implement / verify / memory-update skill workflows. These are adapted to the LaTeX artifact context (stars → existing LaTeX sections; tests → grep + structural checks; deployment → clean-rebuild reproducibility; maintainability → tag format + pattern adherence).

## Key Technical Decisions

Tracked in `architecturalDecisions.md`. Notable additions since the v2 work:
- ADR-003 (implicit) — adopt inline `% [RF-<n>]` traceability tags as the canonical mechanism for connecting reviewer feedback to LaTeX edits
- ADR-004 (implicit) — file-split layout for `proposal_18E/` (milestones, data_sources, decision_gate as separate `\input`-ed files)
- ADR-005 (implicit) — scaling-behavior AI advantage claim with empirically-discovered thresholds, replacing first-pass numeric commitments

## Constraints

- Abstract: 1-page maximum (excluding references) — **SUBMITTED** 2026-03-27
- Full proposal: 5 pages plus references — **DUE** 2026-04-28
- Body currently 6 pages (1 over) — page-budget session 2026-04-10
- Project duration: 1 year starting 2026-07-01
- Must align with U.S. Department of Energy mission and Executive Order 14363 (Genesis Mission)

---

**Note:** Update when tech stack, build process, or external dependencies change.
