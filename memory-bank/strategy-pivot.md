# Strategy Notes (March 14, 2026)

## Current Workflow: Polish All 3 → Review → Select → Submit

All three proposals will be polished to submission-ready quality. Each will go through a reviewer process for feedback. Final selection of which 2 to submit will be based on review outcomes.

| Rank | Proposal | CFP Topics | Status |
|---|---|---|---|
| **#1** | **PA-AKG** (v2) | Knowledge Grounding + Agentic AI | Polishing — highest ranked, safest bet |
| **#2** | **AKG-E** (v4) | AI for Science & Engineering + Agentic AI | Polishing — advisor-aligned, distinctive |
| **#3** | **SVF** (v3) | Agentic Evaluation + Responsible AI | Polishing — may go to other venues |

## Why the Pivot

The devil's advocate analysis revealed:

1. **PA-AKG is our strongest proposal by every metric we tracked** — highest reviewer alignment, highest feasibility, highest Amazon relevance per our own deep-research-topics.md scoring
2. **SVF has honest weaknesses** — the "meta" nature (evaluates systems but doesn't build one), overclaimed novelty ("first framework"), underdeveloped coordination reliability dimension
3. **The topic overlap argument was overstated** — "Agentic AI" as secondary is extremely common; different primary topics go to different reviewer pools; PA-AKG and AKG-E are genuinely different proposals
4. **PA-AKG is the most feasible in 1 year** — clearly scoped system with natural ablation points, vs. AKG-E needing 3 domains and SVF needing full benchmark suites

## Advisor Context

- **PA-AKG**: Dr. Brown (co-PI/collaborator) — strong fit for knowledge grounding research
- **AKG-E**: Advisor in Building & Construction department — aligns with her construction.ai initiative and interests in thermal analysis / VVUQ

## AKG-E Reframing Notes

The AKG-E proposal should be reframed around **2 concrete applications** rather than 3 generic domains:

### Application 1: Construction — Material Takeoff with Computer Vision
- Uses **computer vision** for automated material takeoff from construction plans/drawings
- Feeds into BOM (bill of materials) reasoning and cost estimation
- Ties directly into the advisor's **construction.ai** initiative
- KG layer encodes construction domain knowledge (materials, assemblies, building codes)

### Application 2: Transportation — Digital Twin
- Builds a **digital twin** for traffic system modeling and optimization
- Agent reasons over traffic flow models, network topology, and sensor data
- KG layer encodes transportation domain knowledge (network constraints, flow equations)

### Shared Component: VVUQ (Verification, Validation, and Uncertainty Quantification)
- Both applications share **VVUQ** as the simulation/analysis backbone
- Construction: beam load analysis, structural integrity verification
- Transportation: traffic flow simulation, capacity analysis
- Thermal: heat transfer analysis, HVAC sizing (cross-cuts both domains)
- VVUQ provides the rigorous validation layer that distinguishes this from pure LLM approaches

### Why This Framing Is Stronger
- **Less ambitious** — 2 focused applications vs. 4 generic domains
- **More concrete** — CV for material takeoff and digital twins are specific, demonstrable
- **Better advisor alignment** — directly maps to construction.ai work
- **VVUQ as unifying thread** — gives the framework a clear scientific identity beyond "agents + KGs"
- **Addresses AKG-E's weaknesses** — the simulation integration layer is no longer hand-waved; VVUQ is the simulation layer

## Honest Ranking (Likelihood of Funding)

1. **PA-AKG** — strongest topic fit, most feasible, best abstract writing
2. **AKG-E** — most distinctive but needs reframing; VVUQ + 2 applications reduces risk
3. **SVF** — solid but "meta" nature and overclaims weaken it for Amazon specifically

## What NOT to Change Yet

- Do not modify the actual LaTeX abstracts until the direction is confirmed with advisors
- The website should reflect the updated strategy analysis
- PA-AKG should be un-archived on the dashboard
- SVF should be noted as "reserved for other initiatives"

## Key Terms

- **VVUQ**: Verification, Validation, and Uncertainty Quantification — systematic approach to ensuring simulation/model outputs are correct, physically valid, and quantify uncertainty
- **Construction.ai**: Advisor's existing initiative in the Building & Construction department
- **Material takeoff**: Process of quantifying materials needed from construction plans/drawings
- **Digital twin**: Virtual replica of a physical system used for simulation and analysis
