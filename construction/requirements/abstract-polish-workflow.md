# Abstract Polish Workflow

_Created: 2026-03-14_
_Updated: 2026-03-16_

## Workflow Overview

```
~~Polish All 3 Abstracts~~ → Run Reviewer Process → Incorporate Feedback → Select 2 → Submit
```

### Timeline

| Date | Task | Status |
|------|------|--------|
| Mar 14 | Polish all 3 abstracts to submission quality | DONE |
| Mar 14 | Create AKG-E v4b variant (2 domains + VVUQ) | DONE |
| Mar 15 | Create AKG-E v4c variant (construction-only + VVUQ) | DONE |
| Mar 15 | Run reviewer process on all polished abstracts | DONE |
| Mar 16 | PA-AKG advisor revision rounds (multiple) | DONE |
| Mar 16 | Incorporate feedback; decide which 2 to submit | IN PROGRESS — PA-AKG confirmed #1; AKG-E variant TBD |
| Mar 17 | Portal registration and submission (deadline) | Pending |

### Selection Criteria

After the reviewer process, the final 2 will be selected based on:

1. Reviewer feedback quality and concerns raised
2. Strength of novelty claims after polish
3. Amazon/CFP topic alignment
4. Feasibility within 1-year scope
5. Advisor enthusiasm and fit

---

## Proposal 1: PA-AKG — Provenance-Aware Agentic Knowledge Graph Systems

**Rank**: #1 (highest priority)

| Field | Value |
|-------|-------|
| Primary Topic | Knowledge Grounding |
| Secondary Topic | Agentic AI |
| Abstract Version | v2 (abstract_v2.pdf) |
| Current Status | **COMPLETE** — multiple advisor revision rounds on 2026-03-16; PR #12 merged |

### Known Strengths

- Strongest topic fit for CFP (Knowledge Grounding is a core Amazon interest)
- Highest feasibility — clearly scoped system with natural ablation points
- Best abstract writing quality (v2 is SOA-grounded with 2024-2026 citations)
- Strong Amazon relevance (Bedrock, RAG, knowledge management)
- Addresses real gaps: provenance-aware KG grounding + validation loops beyond GraphRAG/CRAG
- Dr. Brown as co-PI/collaborator — strong fit

### Known Weaknesses

- Knowledge Grounding is a competitive topic area — many submissions expected
- "Provenance-aware" framing needs to be clearly differentiated from standard attribution/citation work
- Architecture diagram may be too complex for 1-page abstract

### PA-AKG Polish Changes (Completed)

- [x] Sharpened novelty claims: unified substrate vs isolated capabilities (GraphRAG/CRAG/Self-RAG)
- [x] Added Self-RAG citation to strengthen SOA grounding
- [x] Added concrete evaluation tasks
- [x] Tightened Amazon/Bedrock relevance language
- [x] Verified 1-page fit with references excluded
- [x] Final language polish

### PA-AKG Advisor Revision Rounds (2026-03-16, COMPLETE)

- [x] Added student motivating example (AI research assistant synthesizing literature)
- [x] Added Amazon KG context sentence (Amazon commonsense KG for recommendations)
- [x] Added CFP Knowledge Grounding alignment sentence (explicit topic callout in proposal body)
- [x] Added evaluation rationale sentence (explaining what experiments will reveal)
- [x] Fixed title line break to render correctly in 2 lines
- [x] All changes compiled, deployed, and PR #12 merged

---

## Proposal 2: AKG-E — Agentic Knowledge Graphs for Engineering

**Rank**: #2

| Field | Value |
|-------|-------|
| Primary Topic | AI Accelerated Science & Engineering |
| Secondary Topic | Agentic AI |
| Abstract Versions | v4 (abstract_v4.pdf), v4b (abstract_v4b.pdf), v4c (abstract_v4c.pdf) |
| Current Status | **POLISHED** — concrete sim tools, tightened scope; v4b reframed variant created; v4c construction-only variant created |

### Known Strengths

- Most distinctive proposal — "AI for Science & Engineering" is less crowded than Knowledge Grounding
- Strong advisor alignment — maps to construction.ai initiative
- VVUQ (Verification, Validation, and Uncertainty Quantification) gives scientific rigor
- Two concrete applications: construction material takeoff with CV, transportation digital twin
- Different reviewer pool from PA-AKG (different primary topic)

### AKG-E Known Weaknesses (Post-Polish)

- Even 2 domains + VVUQ is ambitious for 1 year
- Need to decide between v4 (2+1 domains), v4b (2 domains + VVUQ backbone), and v4c (construction-only + VVUQ backbone) before submission

### AKG-E Polish Changes (Completed)

- [x] v4: Added concrete simulation tools (OpenSeesPy, SUMO)
- [x] v4: Tightened prose throughout
- [x] v4: Narrowed focus to 2+1 domains (from 3-4 generic)
- [x] v4b: Created new variant — reframed with 2 focused applications + VVUQ as unifying backbone
- [x] v4c: Created construction-only variant of v4b — narrows to single domain (construction material takeoff with CV) + VVUQ backbone
- [x] Strengthened connection to advisor's construction.ai work
- [x] Polished writing quality to match PA-AKG v2 level
- [ ] Confirm reframing direction with advisor (v4 vs v4b vs v4c) before submission

---

## Proposal 3: SVF — Structured Validation Framework

**Rank**: #3 (may be reserved for other venues)

| Field | Value |
|-------|-------|
| Primary Topic | Foundation Model/Agentic Evaluation |
| Secondary Topic | Responsible Generative AI |
| Abstract Version | v3 (abstract_v3.pdf) |
| Current Status | **POLISHED** — overclaims toned down, coordination developed, scope narrowed |

### Known Strengths

- Addresses growing need for agentic system evaluation
- Combines evaluation + responsible AI — unique angle
- Responsible AI is high priority for Amazon
- Could have broad impact if benchmark suite is adopted

### SVF Known Weaknesses (Post-Polish)

- "Meta" nature — evaluates systems but doesn't build one (less exciting for funders)
- Weaker Amazon-specific relevance compared to PA-AKG

### SVF Polish Changes (Completed)

- [x] Toned down "first framework" claims — positioned as "systematic evaluation framework addressing critical gaps"
- [x] Developed coordination reliability: fault injection, cascading error propagation, recovery latency
- [x] Narrowed scope to 3 concrete task types (retrieval QA, agent workflows, coordination scenarios)
- [x] Strengthened Amazon angle: production agent platform reference added
- [x] Final language polish: "unlike post-hoc benchmarks" framing

---

## Reviewer Process (Mar 15)

Each abstract will be reviewed with the following evaluation criteria:

1. **Novelty**: Is the contribution clearly new and differentiated from SOA?
2. **Feasibility**: Can this be done in 1 year with the stated team?
3. **Amazon Relevance**: Does this align with Amazon's AI research interests?
4. **CFP Fit**: Does this clearly address the stated primary/secondary topics?
5. **Writing Quality**: Is the abstract clear, concise, and compelling?
6. **Impact**: What is the potential for meaningful research contribution?

### Review Output

For each proposal, the reviewer process should produce:

- Numerical scores (1-5) on each criterion
- Top 3 strengths
- Top 3 weaknesses or concerns
- Specific suggestions for improvement
- Go/no-go recommendation for submission

### Decision Framework

After reviews are complete:

- If all 3 are strong: submit PA-AKG (#1) + AKG-E (#2, choosing between v4, v4b, and v4c)
- If AKG-E reviews poorly: consider PA-AKG + SVF
- If only 1 is strong enough: submit just that one (quality over quantity)
