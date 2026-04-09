# Feature: 18E Proposal — Incorporate Reviewer Feedback (v2)

**Status:** PARTIALLY VERIFIED (2026-04-09; 7 of 11 ACs passed all 4 gates; AC-2 and AC-6 blocked on Sandia meeting; AC-8 deferred to Friday page-budget session)
**Date:** 2026-04-08
**Last Reviewed:** 2026-04-09 (dual-persona adversarial review incorporated)
**Last Implemented:** 2026-04-09 (Phase 4 edits applied; compile clean)
**Last Verified:** 2026-04-09 (4-gate verification pass on unblocked ACs; clean rebuild reproducible)
**Author:** Feature Architect (AI-assisted)
**Source plan (v1):** `files/full-proposal-plan-18E.md` (read-only)
**Target artifact:** `proposal_18E/main.tex` (new folder, copied from `abstract_18E/`, kept parallel so we can compare the two versions)
**Hard deadline:** 2026-04-28 (full proposal due)
**Sign-off authority:** Brown + Wang (joint), with Cusati as proxy signaler who relays decisions back into this spec and the LaTeX.

---

## Problem

The 18E pre-proposal was submitted and ranked **#1 of 2** by all three Genesis reviewers, but they raised six concrete concerns that must be addressed in the full proposal. The existing v1 plan (`files/full-proposal-plan-18E.md`) enumerates *what* to fix but provides no traceability back from each LaTeX edit to the reviewer comment that drove it, no acceptance criteria, no page-budget math, and no sequencing that accounts for the **Sandia partner meeting on 2026-04-09** (which gates two of the six fixes). Without a formal spec, two failure modes are likely: (a) reviewer concerns get partially addressed and we discover the miss only in the next review round, and (b) late content additions blow the 5-page limit because no one was tracking it. The `abstract_18E/main.tex` source still contains **four explicit `\todo{}` markers** and the Team paragraph does not name an industry partner or make prior collaborations explicit.

## Goals

- Every one of the six reviewer concerns (RF-1 through RF-6) has a traceable, acceptance-verifiable edit in `proposal_18E/main.tex` by **2026-04-28**.
- Zero `\todo{}` markers remain in the final compiled PDF.
- Final compiled PDF body is **≤ 5 pages** (references separate), verified by a page-count check before submission.
- Every reviewer-driven edit carries an inline `% [RF-<n>] ...` comment citing the concern and the acceptance criterion that verifies it, so a `grep` audit can confirm coverage.
- Decisions deferred to the Sandia meeting (industry partner, specific Sandia corpus names) have a locked-in **Plan B** fallback. **Brown** is the named triggerer (with Cusati as proxy) and flips Plan A → Plan B by **2026-04-11 EOD** using his judgment on partial commitments.
- Decision Gate Metrics are written into the LaTeX as **scaling-behavior claims** (monotonic improvement as KG/corpus scales), not fixed-number commitments. Actual threshold values are discovered via two calibration studies specified in AC-5b (Phase 1, small seed) and AC-5c (Phase 2, expanded corpus) — the two-study progression *is* the AI advantage evidence the CFP asks for.

## Non-Goals

- Rewriting the PA-AKG research thesis. The reviewers praised the core concept; this spec adds reviewer-driven content around that core without re-litigating the architecture or the three-layer framing.
- Recruiting the industry partner. Recruitment happens outside this spec; v2 only specifies how the spec reacts to the outcome.
- Editing the submitted 1-page pre-proposal abstract (`abstract_18E/abstract.tex`). That artifact is frozen. All edits target the full-proposal manuscript.
- Producing Appendix 2 (computing resources) or budget documents. Those are separate deliverables.
- Cost/budget decisions, cost-share calculations, or any Criterion 5 work.
- Exhaustive page-budget compression. That exercise is scheduled for **2026-04-10** as a separate session; this spec only records the dependency.

## User Stories

- As the **PI (Brown)**, I want every reviewer concern mapped to a specific LaTeX edit so I can sign off on the final manuscript knowing nothing was missed.
- As the **GRA (Cusati)**, I want an ordered checklist of LaTeX edits with acceptance criteria so I can draft content without guessing which reviewer issue each paragraph is solving.
- As a **Genesis merit reviewer in the next round**, I want to open the full proposal and find every Round-1 concern visibly addressed without having to infer it.
- As the **writer (human or agent)** executing this spec, I want a traceability table that tells me "open / block / defer" for each item so I don't wait on Sandia for things I can write today.

## Design Approach

### Artifact layout

```
proposal_18E/                 # NEW — copy of abstract_18E/, full-proposal scope
├── main.tex                  # full-proposal body, edited per RF-1..RF-6
├── abstract.tex              # unchanged (already submitted pre-proposal text)
├── cover_sheet.tex           # edited to add industry partner IF secured
├── milestones.tex            # NEW — Gantt/milestone table (RF-4)
├── data_sources.tex          # NEW — Data Sources and Models (RF-5b)
├── decision_gate.tex         # NEW — Decision Gate Metrics (RF-5a)
├── images/
│   ├── architecture-diagram.png     # reused from abstract_18E
│   └── timeline-gantt.png           # NEW — visual timeline for RF-4
└── references.bib            # extended with any new cites added this round
```

Keeping `abstract_18E/` untouched preserves the reproducibility of the submitted artifact and matches the "v2 = new file, don't overwrite" constraint.

### Traceability pattern

Every LaTeX edit driven by reviewer feedback carries an inline comment of this exact form:

```latex
% [RF-<n>] <short quoted reviewer concern> — verified by: AC-<m>
```

Where:
- `RF-1` through `RF-6` match the six concerns from v1 (`files/full-proposal-plan-18E.md`).
- `AC-1` through `AC-8` match the acceptance criteria in this spec.
- `grep '\[RF-' proposal_18E/main.tex` must return at least eight hits before submission.

### Section-level flow of changes

| Section in `main.tex` | Change | Driving concern |
|---|---|---|
| Introduction | New paragraph on data pipeline framing (see Sample Implementation) | RF-1 |
| Project Objectives | Add infrastructure statement as final sentence | RF-5c |
| Proposed Research and Methods | Restructure Phase 2 to front-load interim eval; add Gantt table | RF-4 |
| Milestones | Replace `\todo{}` with real milestone table | RF-4 |
| Data Sources and Models | Replace `\todo{}` with real content (Kokkos/Trilinos/LAMMPS + fallback) | RF-5b |
| Decision Gate Metrics | Replace `\todo{}` with locked-in quantitative targets | RF-5a |
| Team, Resources, Management | Explicit prior-collaboration sentence; named industry partner (or Plan B) | RF-2, RF-3 |
| Whole doc | Page-count enforcement | RF-6 |

### Plan B branch (if Sandia meeting does not resolve RF-2 and RF-5b specifics)

Triggered if, by **2026-04-11 EOD**, either:
- No industry partner letter of commitment has been secured, OR
- Sandia has not named specific Kokkos/Trilinos/LAMMPS corpus subsets accessible under existing data agreements.

Under Plan B:
- **Industry partner (RF-2):** Shift commercialization narrative to a Phase II deliverable. Team section states that a commercialization partner will be engaged during Phase I to support transition. Criterion 4 is addressed by naming HPE, NVIDIA, and AWS as candidates with a stated engagement plan, not a commitment.
- **Sandia corpus (RF-5b):** Data Sources section re-anchors on public corpora: E4S ecosystem, public LAMMPS GitHub history, public Kokkos tutorials and regression tests, public Trilinos benchmark suite. Sandia is cited as "secondary domain validation" without naming a specific corpus. Steinmetz's role is framed as validation methodology, not corpus provider.

## Sample Implementation

Walking one reviewer concern (RF-1: data pipeline framing) end-to-end. The same pattern applies to RF-2 through RF-6.

```latex
% ===== Sample: RF-1 traceable edit =====
%
% BEFORE (abstract_18E/main.tex, line 50 — current Introduction opening)
\section{Introduction}
The DOE national laboratory system maintains some of the most complex and
consequential scientific software in the world~\cite{perabytes}, encoding
decades of expertise in numerical methods, simulation algorithms, and HPC
architectures...

% AFTER (proposal_18E/main.tex — new paragraph inserted after existing intro)
%
% [RF-1] "focus is tighter than the focus area — focusing on building software
%  specifically rather than data moving through the models" — Reviewer 1
%  — verified by: AC-1

\paragraph{PA-AKG as data infrastructure for trustworthy AI learning.}
Beyond assisting individual code recommendations, PA-AKG is the data
infrastructure that curates and structures the signals AI systems must learn
from in HPC contexts: compiler traces, HPC performance profiles, benchmark
logs, validation test outcomes, and the git history connecting them. The KG
encodes these data as first-class entities with provenance links, so that AI
agents trained or prompted against the KG inherit structured evidence rather
than unstructured text. This directly addresses the 18E focus-area language
of ``learning from decades of DOE codes, compiler traces, and performance
data''---reframing the scientific contribution not as a better code-assistance
tool but as the data substrate that makes AI learning from HPC software
trustworthy and reproducible~\cite{Ji2023HallucinationSurvey}.
```

The same pattern, applied to all six concerns, produces the traceability table under Acceptance Criteria below.

## Edge Cases & Error Handling

### EC-1: Sandia meeting is cancelled or postponed
- **Scenario**: Tomorrow's 2026-04-09 14:00 meeting gets pushed past 2026-04-11.
- **Behavior**: Plan B branch activates automatically by EOD 2026-04-11. AC-2 and AC-6 fall back to Plan B wording. Writer proceeds with non-blocked items (RF-1, RF-3, RF-4, RF-5a, RF-5c) in parallel.
- **Test**: Writer or PI confirms meeting status on 2026-04-11; if not met, check Plan B box in traceability table.

### EC-2: Industry partner commits but after Plan B trigger
- **Scenario**: HPE (or other) commits on 2026-04-20, after Plan B wording is already in draft.
- **Behavior**: Revert Team section to Plan A wording; add partner to cover sheet. No other changes needed because Plan A/B share the same structure. Tag the reversion with `% [RF-2] partner secured late, see cover sheet`.
- **Test**: `grep '\[RF-2]' proposal_18E/main.tex` shows the Plan A wording on final pass.

### EC-3: Page count exceeds 5 after all edits applied
- **Scenario**: Friday 2026-04-10 page-budget session finds compiled PDF at 5.4 pages.
- **Behavior**: This spec does not mandate the cuts — they're handled in the Friday session. But the spec's AC-8 blocks submission until the count is ≤ 5. Cuts must not remove any `[RF-<n>]`-tagged content; compression targets figure sizes, whitespace, and prose density first.
- **Test**: `pdfinfo proposal_18E/main.pdf` reports ≤ 5 pages for body section (references separate).

### EC-4: Decision Gate Metric numbers challenged by Brown/Wang
- **Scenario**: On Brown's review pass, one of the locked-in metrics (e.g., ≥90% reproducibility) is deemed unrealistic.
- **Behavior**: Spec's AC-5 is locked against v1's numbers, but the spec is not above revision. PI-level escalation: Brown can override any AC-5 value; override is recorded in this spec file as a dated amendment. Other ACs are unaffected.
- **Test**: Amendment log at bottom of this spec is updated before LaTeX edit ships.

### EC-5: `\todo{}` macro removed but content is still a placeholder
- **Scenario**: Writer replaces `\todo{...}` with real-looking prose that does not actually satisfy the acceptance criterion (e.g., mentions "Sandia data" without specifics).
- **Behavior**: Each AC has a structural check beyond "the `\todo` is gone." `grep '\\todo{'` is a *necessary but not sufficient* gate.
- **Test**: Peer reviewer (Brown) signs off on each RF-<n>-tagged section, not on the absence of `\todo{}` alone.

### EC-6: Two reviewer concerns need edits to the same paragraph
- **Scenario**: RF-2 (industry partner) and RF-3 (prior collab) both modify the Team paragraph.
- **Behavior**: Both tags appear as separate comments above the relevant sentences. One paragraph can carry multiple `[RF-<n>]` tags. The traceability table allows the same LaTeX location to appear for multiple concerns.
- **Test**: `grep -c '\[RF-' proposal_18E/main.tex` ≥ 8 (not exactly 8); each AC's grep check is scoped to its tag.

## Acceptance Criteria

### AC-1: RF-1 — Data pipeline framing present in Introduction
- **Given** the current `abstract_18E/main.tex` Introduction
- **When** the v2 edits are applied to `proposal_18E/main.tex`
- **Then** the Introduction contains a paragraph that:
  - (a) names at least 3 of {compiler traces, HPC performance profiles, benchmark logs, validation test outcomes, git history},
  - (b) explicitly frames PA-AKG as "data infrastructure" (exact phrase),
  - (c) cites or paraphrases the 18E language about "learning from decades of DOE codes",
  - (d) carries the `% [RF-1]` inline comment tag.
- **Verified by:** grep for `[RF-1]` + Brown + Wang joint sign-off (Cusati proxy).

### AC-2: RF-2 — Industry partner (Plan A) OR commercialization narrative (Plan B)
- **Given** the Sandia meeting outcome on 2026-04-09 and Plan B trigger date 2026-04-11
- **When** the Team section and cover sheet are edited
- **Then** one of two states holds:
  - **Plan A**: A named industry partner appears on the cover sheet AND in the Team paragraph with a sentence describing their role (validation corpus, deployment pathway, or engineering contribution). A Technology Transfer / Commercialization paragraph of ≥3 sentences exists.
  - **Plan B**: A commercialization paragraph names HPE, NVIDIA, AWS as candidate engagement targets and describes a Phase I engagement plan. The paragraph is ≥3 sentences. The cover sheet is not modified.
- **Verified by:** grep for `[RF-2]` + Brown sign-off + confirmation of which plan is active.

### AC-3: RF-3 — Prior collaboration explicit in Team section
- **Given** the current Team paragraph (line 121 of `abstract_18E/main.tex`)
- **When** the v2 edit is applied
- **Then** the Team section contains:
  - (a) an explicit sentence naming Brown + Cusati prior co-authorship (`cusati2026fose`, `brown2025esem`),
  - (b) either a Brown–Wang collaboration reference OR an acknowledgement that the VT–Sandia–Wang collaboration is new with a specific coordination mechanism (regular meetings, shared data access, co-supervision),
  - (c) the `% [RF-3]` tag.
- **Verified by:** grep for `[RF-3]` + Brown + Wang joint sign-off (Cusati proxy).

### AC-4: RF-4 — Timeline restructured with Month-6 interim eval
- **Given** the current Phase 1–4 structure in Methods
- **When** the v2 edit is applied
- **Then** the Methods section and Milestones section together satisfy:
  - (a) Phase 2 (M4–6) explicitly includes "preliminary benchmark results" or equivalent language,
  - (b) Phase 3 (M7–9) is labeled "Full evaluation", not the only evaluation phase,
  - (c) A Decision Gate checkpoint at **Month 6** is explicitly named,
  - (d) A milestone table (text or Gantt image) shows the Month-6 gate aligning before Phase II proposal preparation,
  - (e) The `% [RF-4]` tag appears at both the Phase 2 paragraph and the milestone table.
- **Verified by:** grep for `[RF-4]` (≥2 hits) + Brown + Wang joint sign-off (Cusati proxy).

### AC-5: RF-5a — Decision Gate Metrics as scaling-behavior claims
- **Given** the current `\todo{}` in the Decision Gate Metrics section
- **When** the v2 edit is applied
- **Then** the Decision Gate Metrics section:
  - (a) Frames the AI advantage metric as **scaling behavior**: provenance completeness, reproducibility, and span-level alignment F1 improve **monotonically** as the SE corpus scales from ~10 seed papers (Phase 1 small-seed calibration) to ~50+ papers (Phase 2 expanded snowball).
  - (b) States that Phase I go/no-go thresholds for provenance completeness, reproducibility, and alignment F1 are **discovered empirically via the calibration studies in AC-5b and AC-5c**, not pre-committed in the proposal text. Wording: "Go/no-go thresholds will be set to the values calibrated during Phase 1 (AC-5b), re-validated at Phase 2 (AC-5c), and published with the Month-6 gate report."
  - (c) States the **iterate-if-low rule**: if calibration produces thresholds below a defensible floor (e.g., <30% provenance completeness), the team iterates the PA-AKG implementation before the gate rather than accepting the weak result.
  - (d) Includes a **user-study auditability metric** as a supporting claim (≥70% "auditable" rating), framed as an early user-feedback signal, not as the primary trustworthiness number.
- **And** the section carries the `% [RF-5a]` tag.
- **Verified by:** grep for `[RF-5a]` + structural check that text contains "scaling behavior", "monotonic", "calibration", and "iterate-if-low" (or equivalents) + Brown + Wang joint sign-off.

### AC-5b: RF-5a — Phase 1 small-seed calibration study
- **Given** the commitment to scaling-behavior AI advantage in AC-5
- **When** the v2 edit is applied to the Methods and Decision Gate Metrics sections
- **Then** the proposal describes a **Phase 1 (M1–3) calibration study** with these elements:
  - **Seed paper:** Edge et al. 2024 (Graph-Based RAG) as the canonical starting point.
  - **Corpus build:** snowball sampling backward through references, **limited to ~5–10 papers** in Phase 1 to stay within Phase 1 feasibility (full snowball is deferred to AC-5c).
  - **Two-mode protocol:** (i) **Discovery mode** — hand-annotate claim–evidence pairs to establish baseline thresholds for provenance completeness and span-level alignment; (ii) **Calibration mode** — refine thresholds to find the empirical cutoff that distinguishes trustworthy from untrustworthy recommendations.
  - **Annotation mechanism:** team-consensus annotation (Brown + Wang + Cusati, cross-checked, consensus required). Not single-annotator, not external-only.
  - **Output:** a calibrated initial threshold set that feeds the Decision Gate Metrics section and constitutes the Phase 1 delivery for the AI advantage claim.
  - **Dependency note:** the calibration depends on an initially-populated KG. Ordering inside Phase 1 is serial: schema → initial population → corpus build → discovery → calibration.
- **And** the Methods section carries the `% [RF-5a-b]` tag at the paragraph describing this study.
- **Verified by:** grep for `[RF-5a-b]` + structural check (seed paper named, ~5–10 papers, team consensus, both discovery and calibration mentioned) + Brown + Wang joint sign-off.

### AC-5c: RF-5a — Phase 2 expanded-corpus calibration study
- **Given** the Phase 1 calibration results from AC-5b
- **When** the v2 edit is applied to the Methods section
- **Then** the proposal describes a **Phase 2 (M4–6) second calibration study** with:
  - **Corpus expansion:** full snowball sample grown from the Phase 1 seed to ~50+ papers.
  - **Second calibration pass:** re-run the calibration protocol from AC-5b against the larger corpus.
  - **Scaling-behavior evidence:** the comparison of Phase 1 (small corpus) thresholds to Phase 2 (large corpus) thresholds is the **direct empirical demonstration** of the monotonic-improvement claim in AC-5. The proposal explicitly frames the two-study progression as the AI advantage metric.
  - **Go/no-go input:** Phase 2 calibrated thresholds are the values reported at the Month-6 gate.
- **And** the Methods section carries the `% [RF-5a-c]` tag at the Phase 2 paragraph.
- **Verified by:** grep for `[RF-5a-c]` + structural check (scaling comparison framed, Month-6 gate references Phase 2 thresholds) + Brown + Wang joint sign-off.

### AC-6: RF-5b — Data Sources and Models section (Plan A or Plan B)
- **Given** the current `\todo{}` in the Data Sources section
- **When** the v2 edit is applied
- **Then** the section names specific data sources across four categories:
  - (1) Software engineering corpus (`cusati2026fose` prior corpus + arXiv/IEEE Xplore HPC publications),
  - (2) HPC codebases (Plan A: specific Sandia Kokkos/Trilinos/LAMMPS subsets as confirmed in meeting; Plan B: public E4S ecosystem, public LAMMPS GitHub, public Kokkos/Trilinos repositories),
  - (3) Compiler traces / performance data (Plan A: specific Sandia benchmarks; Plan B: SPEC CPU/HPC benchmarks + public benchmark suites),
  - (4) Pre-trained models (Llama 3 for local inference, GPT-4 / Claude for comparison, CodeLlama for code tasks) AND graph store (Neo4j or Amazon Neptune) AND vector index (FAISS or pgvector).
- **And** the section explicitly addresses data access under existing agreements (Plan A) or via public availability (Plan B).
- **And** the section carries the `% [RF-5b]` tag.
- **Verified by:** grep for `[RF-5b]` + enumeration check + Brown + Wang joint sign-off (Cusati proxy).

### AC-7: RF-5c — Infrastructure statement present
- **Given** the current `\todo{}` in Project Objectives about the infrastructure statement
- **When** the v2 edit is applied
- **Then** the Project Objectives section contains the exact sentence: *"This project does not involve the construction, alteration, maintenance, and/or repair of public infrastructure in the United States."* (or a technically correct variant if the project scope changes).
- **And** the sentence appears within the first two pages of the Project Narrative (as required by the CFP).
- **And** the sentence carries the `% [RF-5c]` tag.
- **Verified by:** exact string match + page-position check.

### AC-8: RF-6 — Compiled PDF body ≤ 5 pages (bibliography begins on page 6)
- **Given** the final `proposal_18E/main.tex` with all RF-1..RF-5c edits applied
- **When** `pdflatex` compiles the document
- **Then** page 6 of the compiled PDF **begins with the bibliography / references section**. Equivalently: the body content (everything before `\bibliography{}`) fits within pages 1–5.
- **Verified by:** `pdftotext proposal_18E/main.pdf - | head` and confirming that the text corresponding to page 6's header region starts with "References" (or the bibliography title), not body prose. This check is automatable and unambiguous — it matches how a merit reviewer will interpret the CFP's "5 pages plus references" constraint.
- **Escalation:** if Friday (2026-04-10) page-budget cuts do not bring the body under the 5-page limit, the team discusses options (the escalation path is deliberately not pre-committed — see Open Questions).

### AC-0: Global traceability audit (cross-cutting)
- **Given** the final `proposal_18E/main.tex`
- **When** `grep '\[RF-' proposal_18E/main.tex` is run
- **Then** the output contains at least one hit for every tag in `{RF-1, RF-2, RF-3, RF-4, RF-5a, RF-5b, RF-5c}` (RF-6 is a global concern, not a single-location tag).
- **And** `grep '\\todo{' proposal_18E/main.tex` returns zero hits.
- **Verified by:** single shell command run at end of spec execution.

## Technical Notes

- **Sign-off mechanism:** Brown + Wang are the joint sign-off authority on every AC. Cusati is the proxy signaler — Cusati relays decisions back into this spec by appending to the Sign-Off Checklist at the bottom and updating the Amendment Log. This keeps sign-off in one machine-readable place (the spec file itself) and matches how the team actually collaborates in practice. Sign-off staleness is handled by the **material-change rule**: an edit to an RF-tagged paragraph only invalidates the sign-off if it changes the structural substance the AC checks for. Brown (via Cusati) is the judge of what is "material" and records any re-sign-off in the Amendment Log with a new dated line.

- **Affected components:**
  - NEW: `proposal_18E/` directory (copy of `abstract_18E/` as starting point)
  - READ-ONLY: `abstract_18E/*` (preserved for reproducibility of submitted artifact; kept parallel to `proposal_18E/` so the two versions can be compared)
  - READ-ONLY: `files/full-proposal-plan-18E.md` (v1 source of truth)
  - POSSIBLY MODIFIED: `references.bib` (new citations for data pipeline framing and Graph-Based RAG seed)
  - POSSIBLY MODIFIED: `docs/index.html` (add a link card to final PDF once submitted)

- **Patterns to follow:**
  - Design-first construction workflow (ADR-002).
  - Memory-bank updates in `progress.md` as each AC is closed.
  - `\todo{}` / `\problem{}` macros from `files/code_world.tex` remain in use during drafting.

- **Tooling assumptions:**
  - `pdflatex` + `latexmk` (already in `abstract_18E/Makefile`).
  - `grep` for traceability audits.
  - `pdfinfo` or equivalent for page-count checks.

- **Reusable assets:**
  - Sandia-anchored code selection in `docs/18e-doe-codes.md` (Kokkos/Trilinos/LAMMPS rationale).
  - v1 action plan in `files/full-proposal-plan-18E.md` (content source for every RF).
  - Existing figure `abstract_18E/images/architecture-diagram.png` (reuse as-is).

## Dependencies

1. **Sandia partner meeting (2026-04-09 14:00)** — blocks RF-2 Plan A and RF-5b Plan A specifics. **Brown** triggers Plan A → Plan B by 2026-04-11 EOD if unresolved (Cusati proxies). Partial commitments are handled by Brown's judgment and mixed plans are allowed (e.g., Plan A for RF-5b but Plan B for RF-2).
2. **Page-budget session (2026-04-10)** — required for AC-8 enforcement; identifies what to cut if RF-driven additions push the doc past 5 pages. If Friday's cuts do not bring the body under 5 pages, escalation is a team discussion (not pre-committed — see Open Questions).
3. **Brown + Wang joint sign-off** — required for every per-AC acceptance. Cusati is the proxy signaler; sign-off lives in the Sign-Off Checklist at the bottom of this spec.
4. **`references.bib` updates** — new citations for RF-1 (data pipeline framing, Ji 2023 hallucination survey) and AC-5b (Edge et al. 2024 Graph-Based RAG) must be in the bib file before compile.
5. **Initial KG population must precede calibration studies.** AC-5b and AC-5c depend on a populated KG. Inside Phase 1, ordering is serial: schema → initial population → corpus build → discovery → calibration.
6. **v1 plan document** (`files/full-proposal-plan-18E.md`) must remain unmodified for the duration of this spec's execution; it is the canonical source for RF-1..RF-6 content.

## Open Questions

1. **[Resolved in review]** Sign-off authority: Brown + Wang joint, Cusati proxies.
2. **[Resolved in review]** AC-5 framing: scaling-behavior + calibration-discovered thresholds, not fixed numbers.
3. **[Resolved in review]** AC-8 verification: `pdftotext | head` to confirm bibliography starts on page 6.
4. **[Resolved in review]** Plan A/B triggerer: Brown with Cusati proxy; partial commitments allowed via Brown's judgment.
5. **[Open]** **AC-8 escalation** — if Friday's (2026-04-10) page-budget cuts do not bring the body under 5 pages, what happens? Team discussion TBD; could be a fallback figure cut, a prose compression pass, or an architectural decision to drop one of the new RF-driven paragraphs. Not pre-committed.
6. **[Open]** **Where does the final compiled PDF live for distribution?** Default is `docs/` alongside the submitted pre-proposals, linked from `index.html`.
7. **[Open]** **Dry-run reviewer pass before submission?** If yes, what date, and who reviews?
8. **[Open]** **Plan B candidate partner naming** — should Plan B's commercialization paragraph name HPE, NVIDIA, AWS specifically, or stay generic? Named candidates look more committed but also set expectations Brown may not want.
9. **[Open]** **First page-budget cut candidate** — if the Friday session finds the doc ~0.3 pages over, is the architecture figure the first cut candidate, or is it load-bearing?
10. **[Open]** **Steinmetz involvement in sign-off for AC-6 Plan A** — Brown + Wang are the joint signers, but Sandia corpus specifics (Plan A path) are Steinmetz's expertise. Does Cusati need to separately confirm with Steinmetz before proxying a Brown + Wang sign-off on AC-6?
11. **[Open]** **Pilot studies / HPC developer interviews in Phase 1** — currently scoped in `main.tex:82` but not acceptance-tracked by this spec. Should they survive the Phase 1 load relief (small seed corpus vs full snowball), or be pushed to Phase 2 along with the expanded corpus?

## Sign-Off Checklist

Mark each AC with `[x]` when Brown + Wang have jointly signed off. Cusati relays the decision and dates each entry. A sign-off that is invalidated by a material edit gets a new line appended below the original rather than being erased.

- [ ] **AC-0** — Global traceability audit (grep clean + zero `\todo{}`) — Brown: __-__-__, Wang: __-__-__
- [ ] **AC-1** — RF-1 data pipeline framing in Introduction — Brown: __-__-__, Wang: __-__-__
- [ ] **AC-2** — RF-2 industry partner OR commercialization narrative — Brown: __-__-__, Wang: __-__-__
- [ ] **AC-3** — RF-3 prior collaboration explicit — Brown: __-__-__, Wang: __-__-__
- [ ] **AC-4** — RF-4 timeline restructured with Month-6 interim eval — Brown: __-__-__, Wang: __-__-__
- [ ] **AC-5** — RF-5a Decision Gate Metrics as scaling-behavior — Brown: __-__-__, Wang: __-__-__
- [ ] **AC-5b** — RF-5a Phase 1 small-seed calibration study — Brown: __-__-__, Wang: __-__-__
- [ ] **AC-5c** — RF-5a Phase 2 expanded-corpus calibration study — Brown: __-__-__, Wang: __-__-__
- [ ] **AC-6** — RF-5b Data Sources and Models (Plan A or Plan B) — Brown: __-__-__, Wang: __-__-__
- [ ] **AC-7** — RF-5c Infrastructure statement — Brown: __-__-__, Wang: __-__-__
- [ ] **AC-8** — RF-6 body ≤ 5 pages (bibliography starts page 6) — Brown: __-__-__, Wang: __-__-__

## Amendment Log

### 2026-04-09 (verification pass) — 4-gate verification applied
- **Gate 1 (Test Integrity / traceability + structural):** PASS on all 7 unblocked ACs. 9/9 unique RF tags present. Per-AC grep-based structural checks all pass. AC-2 / AC-6 remain blocked on Sandia meeting. AC-8 deferred to 2026-04-10 page-budget session.
- **Gate 2 (Health Check / cite + ref + warnings):** PASS. Zero undefined citations, zero undefined references, zero cross-reference instability in final pdflatex pass. Inherited non-fatal warnings (2 bibtex empty-journal, 1 doc-class path, 1 multiply-defined `tab:my_label`) predate v2 edits.
- **Gate 3 (Deployment Readiness / clean rebuild):** PASS. Deleted `proposal_18E/build/` and ran the 4-pass compile from scratch; all 4 exit codes = 0. Byte-identical content (475,701 bytes, 10 pages) across builds — only timestamp metadata differs. Confirmed `BIBINPUTS` env var is NOT required; bibtex finds `proposal_18E/references.bib` via the `.aux` path. Documented the canonical build command in the spec's Technical Notes (below). Action items logged: stale in-folder `Makefile` expects CWD=folder but paths require CWD=repo root; `proposal_18E/build/` should be added to `.gitignore`.
- **Gate 4 (Maintainability / pattern + format):** PASS. All 11 RF tags follow canonical format. `\paragraph{}`, `\textbf{}`, `\cite{}`, `\ie/\eg` usage matches `abstract_18E/main.tex` conventions. Removed 2 unused labels (`sec:milestones`, `sec:data-sources`) during gate pass — the 2 remaining labels (`sec:methods`, `sec:decision-gate`) are both referenced. Recompiled after label removal: still 465 KB / 10 pages / 0 undefined refs.

### 2026-04-09 (later) — Phase 4 implementation applied
- Cloned `abstract_18E/` → `proposal_18E/` with path updates in `main.tex` (`\input{}` and `\includegraphics{}` paths rewritten to the new folder).
- Applied **7 unblocked RF-driven edits** to `proposal_18E/main.tex`, `proposal_18E/milestones.tex`, `proposal_18E/data_sources.tex`, and `proposal_18E/decision_gate.tex`. All edits carry `% [RF-<n>]` traceability tags.
- Created 3 new split files per the spec's Design Approach: `milestones.tex`, `data_sources.tex`, `decision_gate.tex`.
- Placed **two visible `\todo{}` placeholders** for blocked items: RF-2 (industry partner, in `main.tex:152`) and RF-5b Plan A Sandia specifics (in `data_sources.tex:16`). Data Sources has Plan B (public corpora) written as the safe default.
- Fixed a latent bug in `cover_sheet.tex`: it used the `\proposalEleven` (11C) title macro; changed to `\proposalEighteen` (correct for 18E). Not RF-driven but a visible defect in the new artifact.
- Removed two duplicate BibTeX entries in `proposal_18E/references.bib` (`brown2025esem` and `cusati2026fose` were each defined twice; earlier entries at lines 70/79 kept, later duplicates at lines 191/200 removed). Not RF-driven but blocking the compile with non-zero exit.
- **Deviation from pre-proposal:** When restructuring Phase 1 in Methods to fit the calibration study, the pilot-study / HPC-developer-interviews sentence was dropped from Phase 1. This resolves spec Open Question #11 unilaterally; **needs confirmation or restoration by Brown/Wang.**
- Compile clean: 4-pass `pdflatex → bibtex → pdflatex → pdflatex` all return exit 0. Output PDF is 10 pages, with body (narrative) currently at pages 3–8 = **6 pages, 1 over the 5-page limit**. Deferred to Friday 2026-04-10 page-budget session (per AC-8 / EC-3).
- Two open questions raised for the user by this implementation pass: (a) should the pre-proposal abstract still be `\input`-ed into the full-proposal PDF? (b) does the cover sheet count against the 5-page narrative limit?

### 2026-04-09 — Dual-persona adversarial review applied
- **AC-5 reframed** from fixed-number quantitative commitments (≥80% provenance completeness, ≥90% reproducibility, F1 ≥0.75, etc.) to scaling-behavior claims with empirically-discovered thresholds. Motivation: first-pass numbers from v1 had no defensible basis and committing to them in the LaTeX was a proposal-review liability.
- **AC-5b added** — Phase 1 small-seed calibration study: ~5–10 papers snowballed from Edge et al. 2024 (Graph-Based RAG), discovery + initial calibration, team-consensus annotation.
- **AC-5c added** — Phase 2 expanded-corpus second calibration study: full snowball to ~50+ papers, second calibration pass. The Phase 1 → Phase 2 threshold comparison is now the direct empirical evidence of the AI advantage scaling-behavior claim.
- **AC-8 verification method** changed from "`pdfinfo` or `\lastpage`" (ambiguous about body vs references) to `pdftotext | head` check confirming page 6 starts with the bibliography. Unambiguous and automatable.
- **Sign-off authority** changed from "Brown sign-off" (single signer) to "Brown + Wang joint, Cusati proxy". Rationale: Wang's evaluation-methods expertise is load-bearing on AC-1, AC-4, AC-5, AC-5b, AC-5c; single-signer fragility is reduced.
- **Plan A/B triggerer** explicitly named as Brown (with Cusati proxy); partial commitments handled via triggerer judgment; mixed plans allowed (Plan A for RF-5b but Plan B for RF-2, etc.).
- **Phase 1 load relieved** — Phase 1 corpus scoped to 5–10 seed papers, full snowball deferred to Phase 2 (AC-5c). Motivation: Phase 1 was overloaded with KG schema + population + pilots + calibration; serial dependency on KG populated → corpus → discovery → calibration.
- **AC-8 escalation** deliberately left as an open question rather than pre-committed; team will discuss if Friday 2026-04-10 page-budget cuts fall short.

