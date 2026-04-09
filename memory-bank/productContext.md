# Product Context: Research Proposal

## Problem Statement

Existing agentic AI research systems face three interdependent gaps identified in prior research (Cusati & Brown, ICSE-FoSE 2026; ESEM 2025):

1. **Architectural capability gap**: No existing system integrates persistent, structured knowledge graphs with autonomous multi-agent research workflows. Systems either maintain structured knowledge without agentic reasoning (KG-RAG), or reason autonomously without enforceable provenance (Denario).
2. **Evaluation gap**: No validated evaluation framework addresses AI-generated research outputs. Existing benchmarks (RAGAS, ARES, TruLens) evaluate isolated RAG components but not compound agentic systems producing cumulative research artifacts.
3. **Provenance/faithfulness gap**: No generalizable mechanism enforces traceable linkage between generated claims and specific supporting evidence — citations exist but span-level grounding does not.

These gaps form a cycle: without persistent knowledge infrastructure, provenance tracking is infeasible; without provenance, rigorous evaluation is impossible; without evaluation criteria, architectural design lacks a target to optimize against.

## Research Approach: PA-AKG (Provenance-Aware Agentic Knowledge Graphs)

PA-AKG is submitted across three DOE Genesis focus areas with a distinct framing per area, all sharing a common three-layer architecture:

1. **Knowledge Representation layer** — persistent hybrid property-graph + vector-index KG encoding domain entities (algorithms, numerical methods, code components, benchmarks, validation results) as first-class nodes with typed semantic relations.
2. **Automation & Extraction layer** — structured prompting produces claim–evidence pairs; span-level alignment ties each claim to character-level source spans; canonicalization auditing normalizes and deduplicates entity references.
3. **Agentic Orchestration layer** — role-specific agents (ranking, continuation, evaluation, synthesis) operating under a **provenance inheritance constraint**: every agent handoff carries a provenance context object that downstream agents must inherit and extend.

**Focus area framings (submitted pre-proposals):**

| Area | Framing | Status |
|---|---|---|
| **18E** | Trustworthy AI for Scientific Software — data infrastructure for HPC code curation, translation, and development | **Primary** — ranked #1/2 by all three reviewers; full proposal in progress |
| **11C** | AI-Accelerated Science — closed-loop discovery: KG encodes current model, divergences trigger hypotheses, confirmed hypotheses update KG | Submitted |
| **19B** | Hypothesis Generation from Multi-Modal Data — canonical KG links claims across literature/experiments/simulations, graph analysis surfaces gaps | Submitted |

## Evaluation Framework (E1–E4)

- **E1** — span-level alignment precision/recall
- **E2** — canonicalization consistency (Cohen's κ)
- **E3** — traceability completeness (% of KG nodes with complete provenance chains)
- **E4** — longitudinal stability across sessions

For 18E specifically, the numeric thresholds for E1–E3 are **empirically discovered** via two calibration studies (Phase 1 small seed ~5–10 papers, Phase 2 expanded snowball ~50+ papers), rather than pre-committed. The Phase 1 → Phase 2 threshold progression constitutes the AI advantage scaling-behavior claim required by the CFP.

**Note:** Update when research approach or focus-area framings change.
