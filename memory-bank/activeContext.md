# Active Context

_Last updated: 2026-03-16_

## Current Phase

**Phase 2e: Final Review & Submission Prep**

**CRITICAL: Abstract submission deadline is TOMORROW — March 17, 2026.**

PA-AKG (abstract_v2) is confirmed as submission #1, pending final citation review (running now). AKG-E variant selection (v4b vs v4c) is pending advisor review. SVF (abstract_v5) is the fallback third option if AKG-E is dropped. All three abstracts have been significantly updated today with advisor edits, deep research synthesis, and site enhancements.

## Current Workflow

**~~Polish All 3~~ → ~~Run Reviewer Process~~ → ~~Incorporate Feedback~~ → Finalize Citations → Select AKG-E Variant → Submit by Mar 17**

| Rank | Proposal | DOE Focus Areas | Status |
|---|---|---|---|
| **#1** | **PA-AKG** (v2) | 19B (Hypothesis Generation) + 18E (Trustworthy AI) | SUBMISSION-READY — provenance-first KG architecture; span-level evidence alignment + canonicalization auditing; E1–E4 evaluation framework (djjay-qualifier); PR #12 merged |
| **#2** | **AKG-E** (v4c) | 11C (Autonomous Labs) + 19B (Hypothesis Generation) | SUBMISSION-READY — construction-only, VVUQ backbone, BIM/IFC, FEA (OpenSeesPy), falsifiable hypothesis; PR #6 merged |
| **#2b** | **AKG-E** (v4b) | 11C (Autonomous Labs) + 19B (Hypothesis Generation) | SUBMISSION-READY — 2 focused domains (construction + transportation) + VVUQ backbone; advisor comparing vs v4c |
| **#3** | **SVF** (v5) | 18E (Trustworthy AI) + 11C (Autonomous Labs) | SUBMISSION-READY — four evaluation dimensions (grounding integrity, provenance traceability, reasoning robustness, coordination reliability); RAGAS/ARES/TruLens baselines; PR #5 merged |

## Current Focus

- [x] Apply advisor edits to PA-AKG (v2) — completed Mar 16 (PR #12)
- [x] Create AKG-E v4c (construction-only) — completed Mar 15/16 (PR #6)
- [x] Create SVF v5 from deep research synthesis — completed Mar 16 (PR #5)
- [x] Deploy SVF deep research HTML page (docs/svf-deep-research.html)
- [x] Deploy AKG-E deep research HTML page (docs/deep-research-akge.html)
- [x] Add citation tooltips to all 3 proposal pages
- [x] Add keywords section to AKG-E proposal page
- [x] Link all AKG-E variants (v4, v4b, v4c) on downloads and proposal-akge.html
- [ ] **[IN PROGRESS]** Code review of abstract_v2 citations
- [ ] **[DECISION NEEDED]** Select AKG-E variant to submit: v4b vs v4c (advisor reviewing)
- [ ] **[CRITICAL — TOMORROW]** Portal submission by March 17, 2026

## Strategy Pivot (Mar 14)

The devil's advocate analysis revealed key insights that shifted our strategy:

1. **PA-AKG is our strongest proposal** — highest reviewer alignment, feasibility, and Amazon relevance
2. **SVF has honest weaknesses** — "meta" nature (evaluates systems but doesn't build one), overclaimed novelty
3. **Topic overlap concern was overstated** — different primary topics go to different reviewer pools; PA-AKG and AKG-E are genuinely different proposals
4. **PA-AKG is most feasible in 1 year** — clearly scoped system with natural ablation points

As a result, PA-AKG is ranked #1, AKG-E is #2, and SVF is #3 (reserved for other venues if not submitted).

See `memory-bank/strategy-pivot.md` for full analysis and AKG-E reframing notes.

## Polish Summary (Completed Mar 14)

All abstracts have been polished to submission quality with the following changes:

- **PA-AKG (v2)**: Sharpened novelty framing (unified substrate vs isolated components), added Self-RAG citation, added concrete evaluation tasks
- **SVF (v3)**: Toned down overclaims (removed "first framework" language), developed coordination reliability dimension, narrowed scope to feasible 1-year plan
- **AKG-E (v4)**: Added concrete simulation tools (OpenSeesPy, SUMO), tightened prose throughout, narrowed focus to 2+1 domains
- **AKG-E (v4b)**: New file created as reframed variant with 2 focused application domains + VVUQ as unifying validation backbone

## Research Directions

### PA-AKG — Provenance-Aware Agentic Knowledge Graph Systems (Rank #1)
- Primary DOE Topic: 19B — Hypothesis Generation from Multi-Modal Data
- Secondary DOE Topic: 18E — Trustworthy AI for Scientific Software
- Key framing: Addresses three gaps from qualifying research (djjay-qualifier.pdf): no persistent KG + agentic reasoning, no validated evaluation framework, no generalizable provenance enforcement. Span-level evidence alignment and canonicalization auditing are architectural invariants, not post-hoc annotations. Evaluation axes E1–E4 directly map to 19B's synthesis/hypothesis goals and 18E's trustworthiness requirements.
- Prior work: Brown & Cusati ESEM 2025 (evidence-based beliefs of GenAI tools); Cusati & Brown ICSE-FoSE 2026 (knowledge accumulation in SE research — direct precursor)

### AKG-E — Agentic Knowledge Graphs for Engineering (Rank #2)
- Primary DOE Topic: 11C — AI-Accelerated Science: Correlation to Understanding
- Secondary DOE Topic: 19B — Hypothesis Generation from Multi-Modal Data
- Key framing: VVUQ backbone + simulation-in-the-loop implements 11C's closed-loop discovery paradigm in DOE-relevant engineering domains. CV-based material takeoff (construction) and traffic digital twin (transportation) provide concrete, measurable engineering hypothesis generation tasks aligned with 19B.
- **v4b variant**: 2 focused domains (construction + transportation) + VVUQ as backbone
- **v4c variant**: Construction-only — BIM/IFC, CV material takeoff, OpenSeesPy FEA, tightest 11C alignment

### SVF — Structured Validation Framework (Rank #3)
- Primary DOE Topic: 18E — Trustworthy AI for Scientific Software
- Secondary DOE Topic: 11C — AI-Accelerated Science
- Key framing: Fills the evaluation gap identified in qualifying research — no existing framework evaluates compound agentic systems (RAGAS/ARES/TruLens only cover RAG components). Four dimensions operationalize 18E's requirements: grounding integrity (correctness), provenance traceability (reproducibility), reasoning robustness (diagnostics), coordination reliability (uncertainty quantification).
- Status: May be reserved for other venues if only one submission allowed.

## What's Working

- Project infrastructure complete (memory-bank, construction, agents)
- CFP requirements fully captured
- Abstracts v1-v4 (+ v4b, v4c) complete across 3 proposals (5 submission-ready variants)
- All abstracts polished to submission quality
- Deep research report published on dashboard
- Devil's advocate analysis completed
- Submission strategy analysis completed
- Website restructured with ranked proposal cards and dedicated pages
- GitHub repo, Pages site, and CI pipeline live

## What's Next

- [x] Polish all 3 abstracts to submission quality (completed Mar 14)
- [x] Create AKG-E v4b variant (completed Mar 14)
- [x] Create AKG-E v4c variant (construction-only) (completed Mar 15/16)
- [x] Apply advisor edits to PA-AKG v2 (completed Mar 16)
- [x] Create SVF v5 from deep research synthesis (completed Mar 16)
- [x] Deploy deep research HTML pages for SVF and AKG-E (completed Mar 16)
- [x] Add citation tooltips and keywords to proposal pages (completed Mar 16)
- [ ] Complete citation review for abstract_v2 (in progress)
- [ ] Select AKG-E variant to submit: v4b vs v4c (advisor decision, Mar 16)
- [ ] Portal submission (CRITICAL — March 17, 2026)

## Active Decisions

- **Decided**: PA-AKG (v2) is submission #1 — confirmed; citation review in progress
- **Decided**: PA-AKG ranked #1, AKG-E #2, SVF #3
- **Decided**: Created AKG-E v4b as alternative submission option alongside v4
- **Decided**: Created AKG-E v4c (construction-only) as third AKG-E variant (Mar 15/16)
- **Decided**: SVF v5 created as new synthesis from deep-research-svf.md (Mar 16)
- **Pending**: Which AKG-E variant to submit — v4b (2-domain) or v4c (construction-only); advisor reviewing
- **Pending**: SVF as third option only if AKG-E dropped entirely

## Blockers

- Citation review for abstract_v2 must complete before portal submission
- AKG-E variant decision (v4b vs v4c) needed today — deadline is tomorrow

---

**Note:** Update every session with current status.
