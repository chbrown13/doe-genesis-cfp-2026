# Full Proposal Plan: 18E — Trustworthy AI for Scientific Software
**Due: April 28, 2026 | 5 pages + references**

## Reviewer Summary (18-E Pre-Proposal)

All three reviewers ranked the 18-E pre-proposal **#1** (out of 2). The core concept (PA-AKG), problem statement, and team expertise were praised. The following improvements are required for the full proposal.

---

## Actionable Changes by Reviewer Concern

### 1. Scope: Broaden Beyond "Building the Software"
**Reviewer 1:** *"The focus is somewhat tighter than the focus area (focusing on building the software specifically, rather than on data moving through the models)."*

The 18E focus area explicitly targets AI systems that learn from DOE codes, compiler traces, and performance data — with emphasis on the data pipelines flowing through and training AI models. The pre-proposal focuses almost entirely on the output side (code recommendations), not on the data infrastructure that enables trustworthy AI learning.

**Action items:**
- Add a section or paragraph describing the **data pipeline**: what data feeds into PA-AKG (compiler traces, benchmark logs, HPC performance profiles, git history), how this data is structured, and how it is used to ground/train the AI agents.
- Frame PA-AKG explicitly as a **data infrastructure** for trustworthy AI model development — not just a code assistance tool. The KG is the artifact that curates, structures, and validates the data that AI systems learn from.
- Connect to the 18E language: *"learning from decades of DOE codes, compiler traces, and performance data"* — show PA-AKG as the layer that makes this learning trustworthy and reproducible.
- In the Introduction, add a sentence about how current AI models for code assistance are trained/prompted without structured provenance of their training corpus, and how PA-AKG addresses this gap.

---

### 2. Add an Industry Partner
**Reviewer 1:** *"There is no industry partner to help ensure that the findings are translated into practice."*

This also directly affects Criterion 4 (Commercialization Potential) and Criterion 3 (Team) in the review criteria.

**Action items:**
- Recruit an industry partner with HPC or scientific software interest. Candidates:
  - **HPE (Cray)** — major HPC system vendor with active scientific software interests
  - **Amazon Web Services (HPC/EC2)** — cloud HPC deployments for DOE workloads
  - **NVIDIA** — GPU acceleration for HPC codes; active in AI for scientific computing
  - **A smaller ISV** with existing DOE/national lab contracts
- The partner's role should be clearly defined: e.g., provide real-world HPC codebases for validation, contribute engineering expertise, plan a deployment pathway for PA-AKG in production HPC environments.
- Add a **Technology Transfer / Commercialization** paragraph addressing how the industry partner will translate findings into practice post-project.
- Industry partner should appear on the cover sheet and in the team section.

---

### 3. Clarify Team Prior Collaboration
**Reviewer 1:** *"It is not clear from the proposal whether the team has worked together before."*

**Action items:**
- Add explicit text in the Team section stating prior collaboration: Brown + Cusati co-authored `cusati2026fose` and `brown2025esem`. Note any Brown/Wang collaborations (if any exist).
- If Brown and Steinmetz have not formally collaborated before, acknowledge this and describe how the VT–Sandia collaboration will be structured with concrete coordination mechanisms (regular meetings, shared data access, co-supervision of evaluation at Sandia).
- Cite the Sandia HPC validation corpora that Steinmetz provides access to as tangible evidence of Sandia's committed role.

---

### 4. Fix the Evaluation Timeline
**Reviewer 2:** *"Phase II proposal will be due before the evaluation phase is completed."*

The pre-proposal places all evaluation in Phase 3 (Months 7–9). If the DOE Genesis Phase II proposals are due before evaluation concludes, the go/no-go decision cannot be evidence-based.

**Action items:**
- Restructure the timeline so that **interim evaluation results are available by Month 6** (or earlier), enabling a meaningful Phase II go/no-go decision.
- Suggested restructure:
  - **Phase 1 (M1–3):** KG schema design + initial population + baseline evaluation metrics defined
  - **Phase 2 (M4–6):** Extraction pipeline + agentic orchestration + **preliminary benchmark results** (provenance completeness on small corpus)
  - **Phase 3 (M7–9):** Full evaluation (user studies, cross-domain Sandia validation) + dissemination
  - **Decision Gate:** Define explicit go/no-go metrics evaluable at **Month 6** (see Section 5 below)
- Add a Gantt chart or milestone table showing how the go/no-go decision point aligns with Phase II proposal preparation.

---

### 5. Complete All TODO Sections
The pre-proposal contained explicit TODO markers for required full-proposal sections.

#### 5a. Decision Gate Metrics (currently TODO in pre-proposal)
The review criteria explicitly ask for AI advantage metrics, including scaling behavior.

**Write this section with the following quantitative metrics:**
- **Provenance completeness:** ≥80% of AI-generated code recommendations linked to at least one verifiable evidence node in the KG (baseline: 0% for RAG/GPT-4 baselines)
- **Reproducibility rate:** ≥90% of PA-AKG-recommended transformations reproducible by independent developers following the provenance chain
- **Evidence traceability precision/recall:** span-level alignment F1 ≥0.75 vs. human-annotated ground truth
- **AI advantage metric:** Show scaling behavior — as KG grows (more ingested codes/benchmarks), provenance completeness and recommendation accuracy improve monotonically
- **User study metric:** ≥70% of HPC developers rate PA-AKG recommendations as "auditable" vs. ≤30% for baseline LLM recommendations
- **Go/no-go threshold:** If provenance completeness <60% or reproducibility <75% at Month 6, scope/architecture will be revised before proceeding to full evaluation

#### 5b. Data Sources and Models (currently TODO)
- **Software engineering corpus:** prior work corpus from `cusati2026fose` + arXiv/IEEE Xplore HPC publications
- **HPC codebases:** Sandia National Labs legacy codes, public DOE repositories (LLNL GitHub, E4S ecosystem)
- **Compiler traces / performance data:** Sandia HPC benchmarks; SPEC CPU/HPC benchmarks
- **Pre-trained models:** Llama 3 (local inference for privacy), GPT-4 / Claude (for comparison), CodeLlama (code-specific tasks)
- **Graph store:** Neo4j or Amazon Neptune; vector index via FAISS or pgvector
- **Data access:** VT has existing access to public corpora; Steinmetz provides Sandia data under existing data agreements

#### 5c. Infrastructure Statement (currently TODO)
Add the required statement: *"This project does not involve the construction, alteration, maintenance, and/or repair of public infrastructure in the United States."* (or correct if applicable)

---

### 6. Page Compliance
**Reviewer 2:** *"4 pages instead of 2 [for pre-proposal], which provides an unfair advantage."*

The full proposal allows **5 pages plus references**. Strict compliance is essential — a page limit violation was explicitly flagged in reviews.

**Action items:**
- Set up LaTeX with precise page counting from the start.
- Do not include figures that push content over 5 pages without trimming prose.
- The architecture figure (Fig 1) should be retained but sized to not consume excessive space.
- References go in a separate section (not counted against 5 pages).

---

## Full Proposal Section Outline

| Section | Content | Target Length |
|---------|---------|--------------|
| Introduction | Problem statement + software trustworthiness gap + data pipeline framing | ~0.75 page |
| Project Objectives | PA-AKG goals + AI advantage + alignment with 18E | ~0.5 page |
| Proposed Research and Methods | 3 phases with timeline fix; PA-AKG architecture; data pipeline | ~1.75 pages |
| Milestones | Milestone table with responsible PI and month | ~0.25 page |
| Data Sources and Models | Specific datasets, models, access details | ~0.5 page |
| Decision Gate Metrics | Quantitative go/no-go metrics + scaling behavior | ~0.5 page |
| Team, Resources, Management | Prior collaborations explicit; industry partner; roles | ~0.75 page |
| **Total** | | **5 pages** |

---

## Additional Strategic Recommendations

- **Domain anchor:** Reviewers for 18E already accepted the HPC framing. Reinforce with 1–2 specific named DOE codes or scientific domains (e.g., NWChem, OpenMC, AMReX) to show concreteness without over-promising.
- **Distinguish from pure RAG:** Emphasize that PA-AKG provides *architectural guarantees* (provenance enforced at every agent handoff) vs. RAG which is a best-effort retrieval layer — this sharpens the AI advantage claim.
- **Existing codebase:** The pre-proposal mentioned no existing stack to build on (a concern raised for the 11C proposal). For 18E, explicitly name existing tools: Neo4j for graph storage, LangGraph or CrewAI for agent orchestration, existing SE research corpus from prior Brown/Cusati work. This de-risks feasibility concerns.
- **Sandia role specificity:** Make Steinmetz's role concrete — which specific Sandia codebases or benchmarks will be used? What is the validation protocol? This strengthens Criterion 3.

---

## Priority Order for Writing

1. Fix and write **Decision Gate Metrics** — this was a TODO and directly addresses the timeline concern
2. Write **Data Sources and Models** — another TODO, grounds the feasibility
3. Revise **Methods** to restructure timeline (front-load evaluation milestones)
4. Add **industry partner** to Team section + cover sheet
5. Add explicit **prior collaboration** text in Team section
6. Broaden **Introduction** to frame PA-AKG as data infrastructure for AI models (not just code assistance output)
7. Add infrastructure statement
8. Final page count check and trim to 5 pages
