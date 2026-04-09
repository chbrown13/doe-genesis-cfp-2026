# System Patterns

## Proposal Development Workflow

### Design-First Pattern (ADR-002)
All proposal content flows through the `construction/` workflow:
1. **Design** → doc in `construction/design/` (using `spec_builder.md` template)
2. **Requirements** → checklist in `construction/requirements/` (using v2 construction-spec template for feature-style work)
3. **Sprint** → tasks in `construction/sprints/`
4. **Execute** → write LaTeX content per the acceptance criteria
5. **Validate** → 4-gate verification (test integrity, health check, deployment readiness, maintainability)

### Constellize Skill Workflow (introduced 2026-04-09)
For any non-trivial proposal feature, the three-skill chain runs in order:
1. `/constellize:feature:specify` — adversarial interview + dual-persona review → writes spec to `construction/requirements/<feature>.md` with status `SPECIFIED`
2. `/constellize:feature:implement` — star-gap-generate → creates LaTeX edits with traceability tags; status → `PARTIALLY IMPLEMENTED` or `IMPLEMENTED`
3. `/constellize:feature:verify` — 4 gates on unblocked ACs; status → `PARTIALLY VERIFIED` or `VERIFIED`

The skills were adapted for LaTeX artifacts (see techContext.md for gate translation mapping).

### Memory-Bank Pattern
Living documentation maintained across:
- `projectbrief.md` — scope and deliverables (rarely changes)
- `productContext.md` — research problem and PA-AKG approach
- `techContext.md` — LaTeX toolchain, bib conventions, build commands
- `systemPatterns.md` — this file; conventions and patterns
- `architecturalDecisions.md` — ADRs for non-obvious decisions
- `progress.md` — task tracking per phase
- `phases.md` — phase coordination hub
- `activeContext.md` — current session state (lightweight, updated per session)

## Traceability Pattern (introduced v2, 2026-04-09)

Every LaTeX edit driven by reviewer feedback carries an inline comment of this exact form:
```latex
% [RF-<n>] <short quoted reviewer concern> — verified by: AC-<m>
```
- `RF-<n>` matches the reviewer concern ID from the source plan (e.g., `RF-1`, `RF-5a-b`).
- `AC-<m>` matches the acceptance criterion ID in the v2 spec.
- **Audit command**: `grep '\[RF-' proposal_18E/` must return at least one hit for every required tag.
- **`\todo{}` hygiene**: `grep '\\todo{' proposal_18E/main.tex` returns 0 at final submission. Visible `\todo{}` markers during drafting are acceptable *only* for blocked items, and each must describe exactly what is pending and why.

This pattern originated for the 18E reviewer-feedback incorporation work and is documented at length in `construction/requirements/18E-proposal-incorporate-reviewer-feedback-v2.md`.

## Plan A / Plan B Branching (introduced v2, 2026-04-09)

When a reviewer-driven edit depends on an external event (e.g., a Sandia meeting outcome), the spec defines **Plan A** (event resolved favorably) and **Plan B** (fallback) with an explicit triggerer (a named person), a trigger deadline, and a mixed-plan allowance (Plan A for some RFs, Plan B for others). Plan B is drafted first as the no-regret default so writer work isn't wasted if the event slips.

## Sign-Off Proxy Pattern (introduced v2, 2026-04-09)

Joint Brown + Wang sign-off is required for every v2 acceptance criterion, with Cusati acting as proxy who relays decisions into the spec's Sign-Off Checklist. Sign-off staleness is governed by the **material-change rule**: an edit to an RF-tagged paragraph invalidates prior sign-off only if it changes the structural substance the AC checks for. This keeps sign-off in one machine-readable place (the spec file) and matches how the team actually collaborates.

## Proposal Structure Pattern

### Pre-Proposal Abstract (1 page, already submitted for 11C / 18E / 19B)
- Research problem and motivation
- PA-AKG approach and the three-layer architecture
- Expected outcomes and AI advantage framing
- Topic area alignment

### Full Proposal (5 pages + references)
Section structure (live in `proposal_18E/main.tex`):
1. Introduction (~0.75 pg) — trustworthiness gap + data pipeline framing (RF-1)
2. Project Objectives (~0.5 pg) — PA-AKG goals + infrastructure statement (RF-5c)
3. Proposed Research and Methods (~1.75 pg) — 3 phases with Month-6 interim eval (RF-4); Phase 1 + Phase 2 calibration studies (RF-5a-b, RF-5a-c)
4. Milestones (~0.25 pg) — text table with Month-6 Decision Gate (split file: `milestones.tex`)
5. Data Sources and Models (~0.5 pg) — four-category enumeration with Plan A/B fallback (split file: `data_sources.tex`)
6. Decision Gate Metrics (~0.5 pg) — scaling-behavior AI advantage claims (split file: `decision_gate.tex`)
7. Team, Resources, Management (~0.75 pg) — prior collaborations explicit (RF-3), industry partner (RF-2)
8. References (separate page, not counted toward 5-page limit)

**Split-file layout**: `milestones.tex`, `data_sources.tex`, `decision_gate.tex` live alongside `main.tex` in `proposal_18E/` and are `\input`-ed into the main document. This was chosen during v2 planning to make parallel writing easier; it is specific to v2 and not applied to the pre-proposal abstract.

## Quality Patterns

- **CFP Alignment Check**: Every section maps to a CFP topic area; every reviewer-driven edit carries an RF tag.
- **Grep-Based Coverage**: The LaTeX source is verifiable via `grep` commands listed in the v2 spec's acceptance criteria (structural checks beyond "the \todo is gone").
- **Clean-Slate Rebuild**: Any compile artifact must be reproducible from scratch (`rm -rf build/ && 4-pass compile`).
- **Novelty Validation**: Claims cross-checked against prior PA-AKG work (`cusati2026fose`, `brown2025esem`, qualifying paper).
- **Feasibility Review**: 1-year timeline, Phase 1 load-relieved during v2 review (small seed corpus in Phase 1, full snowball deferred to Phase 2).
- **DOE/Genesis Alignment**: Every section maps to the CFP and Executive Order 14363 language.

---

**Note:** Update as new patterns are introduced or existing ones evolve.
