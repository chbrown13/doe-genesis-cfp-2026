# Architectural Decisions

## ADR-001: Memory-Bank Documentation Structure

- **Status**: Accepted
- **Date**: 2026-03-05
- **Context**: Need a systematic way to track proposal development context, decisions, and progress across sessions.
- **Decision**: Adopt the memory-bank documentation pattern from the construction-ai-proposal project, adapted for CFP workflow.
- **Consequences**: Consistent documentation, easy onboarding between sessions, clear audit trail of decisions.

## ADR-002: Design-First Proposal Development

- **Status**: Accepted
- **Date**: 2026-03-05
- **Context**: Proposal content needs to be well-structured and aligned with CFP requirements before drafting.
- **Decision**: Use construction/ folder with design-before-writing workflow. All proposal sections get a design document before content is drafted.
- **Consequences**: Higher quality output, fewer rewrites, clear traceability from requirements to content.

## ADR-003: Inline `[RF-<n>]` Traceability Tags in LaTeX

- **Status**: Accepted
- **Date**: 2026-04-09
- **Context**: After the 18E pre-proposal review round, six reviewer concerns needed to be addressed in the full proposal. Without an explicit traceability mechanism, there was no way to audit whether every concern had been materially addressed at submission time, and reviewers in the next round could not easily confirm the fixes.
- **Decision**: Every LaTeX edit driven by reviewer feedback carries an inline comment of the exact form `% [RF-<n>] <short reviewer concern> — verified by: AC-<m>`. The tag IDs (`RF-1` through `RF-5c`) match the concerns enumerated in the v1 source plan, and the AC IDs match the acceptance criteria in the v2 construction spec.
- **Consequences**:
  - `grep '\[RF-' proposal_18E/` audits coverage in one command.
  - Traceability survives into the LaTeX source (invisible to rendered PDF readers but preserved for future maintainers).
  - Reviewers in the next round can open the source and immediately see what was added for which concern.
  - Adds ~1 line of overhead per edit; negligible cost for the audit benefit.

## ADR-004: Split-File Layout for `proposal_18E/`

- **Status**: Accepted
- **Date**: 2026-04-09
- **Context**: The v2 spec's Design Approach listed separate files for Milestones, Data Sources, and Decision Gate Metrics. During Phase 3 implementation planning I initially considered collapsing to a single `main.tex`, but the user explicitly chose the split layout for parallel writing and cleaner diff reviews.
- **Decision**: Extract `milestones.tex`, `data_sources.tex`, and `decision_gate.tex` as separate files in `proposal_18E/`, `\input`-ed from `main.tex` at the relevant section boundaries. `main.tex` still owns the Introduction, Project Objectives, Methods, and Team sections directly.
- **Consequences**:
  - Multiple writers (human or agent) can edit different sections without merge conflicts.
  - RF-tagged edits are naturally scoped to one file each.
  - Slightly more indirection than a monolithic main.tex; acceptable for a 5-page document with multiple authors.

## ADR-005: Scaling-Behavior AI Advantage with Empirically-Discovered Thresholds

- **Status**: Accepted
- **Date**: 2026-04-09
- **Context**: The v1 plan committed to specific numeric targets for the Phase I go/no-go (≥80% provenance completeness, ≥90% reproducibility, F1 ≥0.75, ≥70% auditability). These were first-pass estimates with no defensible basis, and committing to them in the LaTeX was a proposal-review liability — a Phase II reviewer could easily ask "what's the basis for 80%?" and the honest answer was "it was a guess".
- **Decision**: Reframe the Decision Gate Metrics section around **scaling behavior** (monotonic improvement of provenance completeness, reproducibility, and alignment F1 as the SE corpus grows from ~10 seed papers to ~50+ papers) with thresholds **discovered empirically** via two calibration studies: AC-5b (Phase 1 small seed, Graph-Based RAG seed with snowball) and AC-5c (Phase 2 expanded corpus, second calibration pass). The Phase 1 → Phase 2 threshold progression constitutes the direct empirical evidence of AI advantage. An **iterate-if-low rule** protects integrity: if calibration produces thresholds below a defensible trustworthiness floor, the team iterates the PA-AKG implementation rather than accepting the weak result.
- **Consequences**:
  - Matches the CFP's explicit request for "scaling behavior which shows increasing performance as additional data, computing, and/or other resources are applied" — now backed by empirical evidence from the two-phase study, not a claim.
  - Eliminates the "where did 80% come from?" review vulnerability.
  - Adds two new acceptance criteria (AC-5b, AC-5c) with their own Phase 1 / Phase 2 sub-commitments.
  - Requires team-consensus annotation (Brown + Wang + Cusati cross-checked) rather than single-annotator calibration.

## ADR-006: Joint Brown + Wang Sign-Off via Cusati Proxy

- **Status**: Accepted
- **Date**: 2026-04-09
- **Context**: The v2 spec's acceptance criteria need a sign-off mechanism. Single-signer (Brown as PI) is fragile — Wang's evaluation-methodology expertise is load-bearing on multiple ACs (AC-1 data pipeline, AC-4 timeline, AC-5 metrics, AC-5b/5c calibration), and if Brown is unavailable in the final week before submission the entire workflow jams.
- **Decision**: Every AC requires joint Brown + Wang sign-off. Cusati acts as proxy signaler, relaying decisions from Brown and Wang into the spec's Sign-Off Checklist. Sign-off staleness is governed by the **material-change rule**: an edit to an RF-tagged paragraph invalidates prior sign-off only if it changes the structural substance the AC checks for; Brown (via Cusati) is the judge of what is "material".
- **Consequences**:
  - Sign-off lives in one machine-readable place (the spec file) rather than scattered across Slack, email, or verbal agreements.
  - Cusati's daily proxy work keeps the process moving without requiring synchronous Brown+Wang availability for every AC.
  - Wang's expertise is baked into the gating mechanism, not relegated to ad-hoc consultation.

## ADR-007: Plan A / Plan B Branching with Named Triggerer

- **Status**: Accepted
- **Date**: 2026-04-09
- **Context**: Two of the six reviewer concerns (RF-2 industry partner, RF-5b Sandia corpus specifics) depend on the outcome of a 2026-04-09 Sandia meeting that happens mid-implementation. Silent persistence (nobody checks, writer drafts wrong content) and ambiguous outcomes (partial commitment) are both real failure modes.
- **Decision**: For each externally-gated item, the spec defines **Plan A** (favorable outcome) and **Plan B** (safe fallback), with (a) Brown as the **named triggerer**, (b) a hard trigger deadline (2026-04-11 EOD), (c) permission for Brown to use judgment on partial commitments and allow mixed plans (Plan A for some RFs, Plan B for others), and (d) Plan B drafted first as the no-regret default so writer work isn't wasted if the event slips. Cusati proxies the Plan A/B decision into the spec Amendment Log.
- **Consequences**:
  - Eliminates silent-persistence bugs by naming a responsible person and a deadline.
  - Writer can start on non-blocked items immediately, placing visible `\todo{}` markers at Plan A/B swap sites.
  - Partial commitments (e.g., Sandia agrees on LAMMPS but not Trilinos) can be handled gracefully via mixed-plan rules rather than forcing a binary choice.

---

_New decisions are appended as ADR-NNN. Superseded decisions are archived._
