# Product Context: Research Proposal

## Problem Statement

Existing agentic AI research systems face three interdependent gaps identified in prior research (Cusati & Brown, ICSE-FoSE 2026; ESEM 2025):

1. **Architectural capability gap**: No existing system integrates persistent, structured knowledge graphs with autonomous multi-agent research workflows. Systems either maintain structured knowledge without agentic reasoning (KG-RAG), or reason autonomously without enforceable provenance (Denario).
2. **Evaluation gap**: No validated evaluation framework addresses AI-generated research outputs. Existing benchmarks (RAGAS, ARES, TruLens) evaluate isolated RAG components but not compound agentic systems producing cumulative research artifacts.
3. **Provenance/faithfulness gap**: No generalizable mechanism enforces traceable linkage between generated claims and specific supporting evidence — citations exist but span-level grounding does not.

These gaps form a cycle: without persistent knowledge infrastructure, provenance tracking is infeasible; without provenance, rigorous evaluation is impossible; without evaluation criteria, architectural design lacks a target to optimize against.

## Research Approaches

### PA-AKG (Rank #1) — DOE Topics: 19B (Primary) + 18E (Secondary)
Provenance-first architecture integrating persistent research knowledge graphs with multi-agent orchestration. Three architectural layers:
- **Knowledge representation layer**: persistent research KG where problems, datasets, methods, constraints, and evidence are first-class entities linked by explicit semantic relations
- **Automation & extraction layer**: span-level evidence alignment (claim → source passage linkage) + canonicalization auditing (entity resolution to canonical KG nodes)
- **Agentic orchestration layer**: ranking agents (prioritize by tractability/evidence strength), continuation agents (propose follow-on analyses), evaluation agents (execute reproducible workflows), synthesis agents (write back structured artifacts)

Key invariant: provenance enforcement is architectural, not post-hoc — every agent handoff carries provenance constraints requiring downstream agents to inherit and extend evidence chains.

Evaluation framework (E1–E4): span-level evidence alignment (precision/recall vs. human-annotated gold), canonicalization consistency (Cohen's κ vs. expert clusters), traceability completeness (% nodes with complete provenance chains), persistence over time (stability score across evolving corpus).

### AKG-E (Rank #2) — DOE Topics: 11C (Primary) + 19B (Secondary)
Agentic KG digital twins for engineering domains, unified by a VVUQ (Verification, Validation, Uncertainty Quantification) backbone:
- **Construction domain**: CV-based material takeoff from BIM/drawings → KG-encoded domain knowledge (materials, assemblies, building codes) → structural verification (OpenSeesPy FEA)
- **Transportation domain**: traffic digital twin → KG-encoded network topology/flow constraints → simulation validation (SUMO)
- VVUQ layer ensures simulation outputs are numerically correct, physically valid, and uncertainty-quantified before agent outputs are accepted

Implements DOE 11C's closed-loop discovery paradigm: AI integrates directly into experimental/engineering workflow, combining real-time analysis, intelligent feedback, and hypothesis generation.

### SVF (Rank #3) — DOE Topics: 18E (Primary) + 11C (Secondary)
Structured Validation Framework measuring four dimensions of knowledge-grounded and multi-agent AI systems:
- **Grounding integrity**: correctness of retrieval-to-claim linkage
- **Provenance traceability**: completeness of evidence chains
- **Reasoning robustness**: performance under adversarial/incomplete retrieval
- **Coordination reliability**: multi-agent failure modes and cascade detection

Directly operationalizes 18E requirements: provenance completeness score (numerical correctness proxy), canonicalization consistency (reproducibility metric), and OpenTelemetry-aligned trace outputs (interpretable performance diagnostics).

## CFP Alignment

| Proposal | Primary Topic | Secondary Topic | Core Connection |
|---|---|---|---|
| PA-AKG | 19B — Hypothesis Generation from Multi-Modal Data | 18E — Trustworthy AI for Scientific Software | Synthesizes SE literature + empirical data to identify research gaps and generate traceable hypotheses |
| AKG-E | 11C — AI-Accelerated Science: Correlation to Understanding | 19B — Hypothesis Generation from Multi-Modal Data | Simulation-in-the-loop VVUQ harness implements closed-loop engineering discovery |
| SVF | 18E — Trustworthy AI for Scientific Software | 11C — AI-Accelerated Science | Four evaluation dimensions directly satisfy 18E trustworthiness requirements |

## Target Audience

### U.S. Department of Energy Reviewers
- Looking for: AI that accelerates scientific discovery and R&D workflows, with clear DOE relevance and Genesis Mission platform integration potential
- Value: practical impact, scalability, national security/energy alignment
- Expect: clear methodology, feasibility within Phase I (9 months), strong technical foundation

### Academic Community
- Looking for: research contributions and publishable outcomes
- Value: novelty (provenance as architectural invariant, not post-hoc), rigor (E1–E4 evaluation axes), reproducibility (artifacts: KG snapshots, agent logs, provenance chains)
- Expect: grounding in literature (Denario, KG-RAG, RAGAS/ARES/TruLens baselines), clear evaluation plan

## Value Proposition

PA-AKG reframes provenance from a "reporting guideline" into foundational research infrastructure — making it a prerequisite for accountable AI-assisted research ecosystems. Unlike existing systems that either maintain structured knowledge without agentic reasoning or reason autonomously without enforceable provenance, PA-AKG enforces span-level evidence alignment as an architectural constraint across all three layers.

## Competitive Landscape

| System | Structured KG | Agentic Reasoning | Provenance Enforcement | Cumulative Learning |
|---|---|---|---|---|
| KG-RAG (Suryawanshi et al.) | ✓ | ✗ | Partial | ✗ |
| Denario (Villaescusa-Navarro et al.) | ✗ | ✓ | ✗ | ✗ |
| PA-AKG (proposed) | ✓ | ✓ | ✓ (architectural) | ✓ |

SVF addresses the evaluation gap that all three above systems share: single-expert scoring without inter-rater reliability, baselines, or operationalized quality definitions.

---

**Note:** Update when proposal content changes.
