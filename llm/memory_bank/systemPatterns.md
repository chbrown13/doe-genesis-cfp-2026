# System Patterns

## Architecture overview

This repository is a **document-authoring workspace**, not a software system. The "architecture" is the workflow and conventions that govern how proposals are specified, drafted, verified, and submitted. No runtime, no services, no APIs. The three durable pillars are:

1. The **memory-bank** (this folder tree) — living documentation updated as work progresses
2. The **construction workflow** — design-first spec → implement → verify cycle for non-trivial proposal features
3. The **LaTeX authoring tree** — one `abstract_<area>/` per focus area (frozen post-submission) and `proposal_<area>/` for active full-proposal work

## Directory layout and what lives where

| Location | Purpose |
|---|---|
| `llm/memory_bank/` | **This folder.** 5 canonical memory files (projectbrief, techContext, systemPatterns, activeContext, progress) |
| `llm/features/` | Spec artifacts produced by `/constellize:feature:specify` |
| `memory-bank/` | Legacy memory bank (parallel to `llm/memory_bank/`, kept temporarily during transition) |
| `llm/features/` | Feature spec files produced by `/constellize:feature:specify` (e.g., `18E-proposal-incorporate-reviewer-feedback-v2.md`) |
| `construction/requirements/` | Legacy location for requirements checklists; retained for non-feature-style work (e.g., `abstract-polish-workflow.md`) |
| `construction/design/` | Design documents (pre-spec brainstorming) |
| `construction/sprints/` | Sprint plans (task breakdowns from specs) |
| `abstract_<area>/` | Frozen pre-proposal LaTeX for each focus area — do not edit after submission |
| `proposal_<area>/` | Active full-proposal workspace for each invited focus area |
| `docs/` | GitHub Pages dashboard for stakeholder visibility |
| `files/` | CFP document, review criteria, prior plans, shared LaTeX macros, the NSF class file |
| `.claude/agents/` | Custom Claude Code agents |
| `.claude/skills/` | Constellize skill workflows (specify, implement, verify, memory:*) |

## Design-First Proposal Development (ADR-002)

All non-trivial proposal content flows through `construction/`:

1. **Design** — doc in `construction/design/` (using `construction/spec_builder.md` as a template) OR for feature-style work, directly to step 2.
2. **Spec** — feature spec in `construction/requirements/<name>.md` written via `/constellize:feature:specify` with status `SPECIFIED`.
3. **Implement** — LaTeX or memory-bank edits via `/constellize:feature:implement`; status → `PARTIALLY IMPLEMENTED` or `IMPLEMENTED`.
4. **Verify** — 4-gate verification via `/constellize:feature:verify`; status → `PARTIALLY VERIFIED` or `VERIFIED`.
5. **Execute** — the proposal content ships (PR merge, submission to DOE portal, etc.).
6. **Validate** — cross-check against CFP requirements, 5-page limit, sign-off checklist.

Rule: no proposal content is drafted without an approved design document or spec.

## Inline RF-Tag Traceability Pattern (ADR-003, introduced 2026-04-09)

Every LaTeX edit driven by external reviewer feedback carries an inline comment of **exactly** this form:

```latex
% [RF-<n>] <short quoted reviewer concern> — verified by: AC-<m>
```

Where:
- `RF-<n>` matches the reviewer concern ID from the v1 source plan (e.g., `RF-1`, `RF-5a-b`)
- `AC-<m>` matches an acceptance criterion in the v2 construction spec

**Audit command**: `grep '\[RF-' proposal_18E/` must return at least one hit for every required tag at verification time.

**`\todo{}` hygiene**: `grep '\\todo{' proposal_18E/main.tex` returns 0 at final submission. Visible `\todo{}` markers during drafting are acceptable *only* for blocked items, and each must describe exactly what is pending and why.

**Canonical example**: see `proposal_18E/main.tex:66` — the RF-1 data pipeline framing tag and paragraph.

## Split-File LaTeX Layout for Full Proposals (ADR-004)

The `proposal_18E/` workspace uses a split-file layout for content sections that see heavy reviewer-driven edits or parallel writing:

- `main.tex` — owns Introduction, Project Objectives, Methods, Team sections directly
- `milestones.tex` — RF-4 milestone table, `\input`-ed from main
- `data_sources.tex` — RF-5b Data Sources section, `\input`-ed from main
- `decision_gate.tex` — RF-5a Decision Gate Metrics, `\input`-ed from main

Rationale: multiple writers can edit different sections without merge conflicts, and RF-tagged edits are naturally scoped to one file each. Only applied to v2 full proposals, not to pre-proposal abstracts.

## Scaling-Behavior AI Advantage Pattern (ADR-005)

For DOE Genesis proposals, the required "AI advantage metric" is framed as **monotonic improvement as corpus/compute scales**, not as a fixed-number commitment. Specifically for 18E:

- **Phase 1 small-seed calibration** (AC-5b) — ~5–10 software engineering papers snowballed from Graph-Based RAG (Edge et al. 2024). Discovery + calibration modes. Team-consensus annotation (Brown + Wang + Cusati, cross-checked).
- **Phase 2 expanded-corpus calibration** (AC-5c) — full snowball to ~50+ papers. Second calibration pass.
- **The Phase 1 → Phase 2 threshold progression IS the empirical AI advantage evidence.** Thresholds themselves are *discovered*, not pre-committed in the LaTeX.
- **Iterate-if-low rule**: if calibration produces thresholds below a defensible trustworthiness floor, the team iterates PA-AKG rather than accepting the weak result. This protects the scaling-behavior claim from being gamed.

## Plan A / Plan B Branching with Named Triggerer (ADR-007)

When a reviewer-driven edit depends on an external event (e.g., a Sandia meeting, an industry partner commitment), the feature spec defines:

- **Plan A** — favorable outcome (e.g., industry partner secured, Sandia corpus confirmed)
- **Plan B** — safe fallback (e.g., public corpora only, Phase II commercialization commitment)
- **Named triggerer** — one person (e.g., Brown) who flips Plan A → Plan B by a hard deadline
- **Judgment allowance** — partial commitments can be handled as mixed plans (Plan A for some RFs, Plan B for others)
- **No-regret default** — Plan B content is drafted first, so writer work isn't wasted if the event slips

Visible `\todo{}` markers sit at Plan A/B swap sites until the trigger fires.

## Joint Sign-Off via Proxy Pattern (ADR-006)

For the 18E v2 work:

- **Authority**: Brown + Wang sign off jointly on every acceptance criterion
- **Proxy**: Cusati relays decisions into the spec's Sign-Off Checklist (single source of truth, lives in the spec file)
- **Staleness rule**: the **material-change rule** — sign-off is invalidated by a later edit only if the edit changes the structural substance the AC checks for. Brown (via Cusati) judges what is "material".

Rationale: single-signer fragility is reduced; Wang's evaluation-methodology expertise is baked into the gating mechanism; sign-off lives in one machine-readable place rather than scattered across Slack, email, or verbal.

## Constellize Skill Workflow

For non-trivial features, run the three-skill chain in order:

1. **`/constellize:feature:specify <name>`** — adversarial interview + dual-persona review → writes spec to `llm/features/<name>.md` (or the project's convention path) with status `SPECIFIED`
2. **`/constellize:feature:implement`** — star-gap-generate → creates edits with traceability tags; status → `PARTIALLY IMPLEMENTED` or `IMPLEMENTED`
3. **`/constellize:feature:verify`** — 4 gates on all acceptance criteria; status → `PARTIALLY VERIFIED` or `VERIFIED`

For memory-bank work, use the memory-update skill directly.

**Adaptation note**: the constellize skills are written assuming a Python code project (`uv run pytest`, `ruff`, `crew`). This is a LaTeX/document project, so the skills are adapted as follows:

| Python gate | LaTeX equivalent |
|---|---|
| Tests + coverage (`pytest --cov`) | Grep RF-tag audit + per-AC structural keyword checks |
| Health check (defensive programming) | Undefined-citation check, undefined-reference check, bibtex warnings, placeholder hygiene |
| Deployment (`uv sync && uv run crew`) | Clean-slate rebuild: `rm -rf build && 4-pass compile`; reproducibility via byte-comparison |
| Maintainability (`ruff check`) | Tag format consistency, pattern adherence (`\paragraph`, `\textbf`, `\cite`), unused labels |

## Proposal Structure Pattern

### Pre-proposal abstract (1 page, already submitted for 11C / 18E / 19B)
- Research problem and motivation
- PA-AKG approach and three-layer architecture
- Expected outcomes and AI advantage framing
- Topic area alignment

### Full proposal (5 pages body + references)
Section structure for 18E (see `proposal_18E/main.tex`):

1. Introduction (~0.75 pg) — trustworthiness gap + data pipeline framing (RF-1)
2. Project Objectives (~0.5 pg) — PA-AKG goals + infrastructure statement (RF-5c)
3. Proposed Research and Methods (~1.75 pg) — 3 phases with Month-6 interim eval (RF-4); Phase 1 + Phase 2 calibration studies (RF-5a-b, RF-5a-c)
4. Milestones (~0.25 pg) — text table with Month-6 Decision Gate (split file: `milestones.tex`)
5. Data Sources and Models (~0.5 pg) — four-category enumeration with Plan A/B fallback (split file: `data_sources.tex`)
6. Decision Gate Metrics (~0.5 pg) — scaling-behavior AI advantage claims (split file: `decision_gate.tex`)
7. Team, Resources, Management (~0.75 pg) — prior collaborations explicit (RF-3), industry partner (RF-2)
8. References (separate, not counted toward 5-page limit)

## Quality patterns

- **CFP Alignment Check**: every section maps to a CFP topic area; every reviewer-driven edit carries an RF tag.
- **Grep-Based Coverage**: LaTeX source is verifiable via `grep` commands listed in the v2 spec's acceptance criteria. Structural keyword checks go beyond "the `\todo` is gone."
- **Clean-Slate Rebuild**: any compile artifact must be reproducible from scratch (`rm -rf build && 4-pass compile` yields byte-identical content modulo timestamp metadata).
- **Novelty Validation**: claims cross-checked against prior PA-AKG work (`cusati2026fose`, `brown2025esem`, Cusati qualifying paper).
- **Feasibility Review**: 1-year timeline, Phase 1 load-relieved during v2 review (small seed corpus in Phase 1, full snowball deferred to Phase 2).
- **DOE/Genesis Alignment**: every section maps to the CFP and Executive Order 14363 language.

## Naming conventions

- **Folders for submission artifacts**: `abstract_<ID>/` for pre-proposals, `proposal_<ID>/` for full proposals (e.g., `abstract_18E/`, `proposal_18E/`)
- **Feature spec files**: `<area>-<feature-description>-v<N>.md` in `construction/requirements/`
- **LaTeX macros for proposal titles**: `\proposalEleven`, `\proposalEighteen`, `\proposalNineteen` — defined in `files/code_world.tex`
- **BibTeX keys**: lowercase, year-suffixed when possible (`brown2025esem`, `cusati2026fose`, `Edge2024GraphRAG`)
- **Branch names**: `feature/<short-description>` (e.g., `feature/18E-proposal-v2`, `feature/memory-bank-update-2026-04-09`)
- **Commit messages**: informal imperative style matching repo history (e.g., "Incorporate 18E pre-proposal reviewer feedback (v2)")

## Architectural Decision Records (summary)

Full ADR details in `memory-bank/architecturalDecisions.md` (legacy path):

| ID | Decision |
|---|---|
| ADR-001 | Memory-bank documentation structure (2026-03-05) |
| ADR-002 | Design-first proposal development via `construction/` (2026-03-05) |
| ADR-003 | Inline `[RF-<n>]` traceability tags in LaTeX (2026-04-09) |
| ADR-004 | Split-file layout for `proposal_18E/` (milestones, data_sources, decision_gate) (2026-04-09) |
| ADR-005 | Scaling-behavior AI advantage with empirically-discovered thresholds (2026-04-09) |
| ADR-006 | Brown + Wang joint sign-off via Cusati proxy with material-change rule (2026-04-09) |
| ADR-007 | Plan A / Plan B branching with named triggerer (2026-04-09) |

---

**Last updated:** 2026-04-09
