# Technical Context

## Research Methodology

### PA-AKG
- Automated claim extraction + structured prompting → claim–evidence pairs (span-level alignment)
- Entity normalization, validation, deduplication → canonicalization auditing
- Hybrid symbolic-semantic design: property graph + vector index (structured filtering + approximate similarity search)
- Multi-agent orchestration adapted from Denario's Planning & Control pattern, extended with provenance inheritance constraints
- Evaluation: precision/recall vs. human-annotated gold spans (E1); Cohen's κ vs. expert entity clusters (E2); % nodes with complete provenance chains (E3); longitudinal stability score (E4)
- Baselines: vector DB + RAG without span alignment; embedding-based clustering; standard RAG without structured provenance; static snapshot-based system
- Primary validation domain: software engineering research corpus; secondary: one additional domain for generalizability

### AKG-E
- CV pipeline for material takeoff from construction drawings/BIM → structured KG
- OpenSeesPy for structural FEA; SUMO for traffic flow simulation
- VVUQ harness: verification (simulation converges), validation (output matches domain benchmarks), uncertainty quantification (propagation through agent decisions)
- Agent types: constraint checkers, simulation invokers, hypothesis generators, validation reporters
- Baselines: prompt-only LLM vs. hybrid KG + agents

### SVF
- Instrumentation-first: OpenTelemetry GenAI spans/traces aligned with semantic conventions
- Four evaluation dimensions: grounding integrity (retrieval-to-claim correctness), provenance traceability (chain completeness), reasoning robustness (adversarial retrieval tests), coordination reliability (cascade failure detection)
- Fault injection benchmark for multi-agent systems (drop tool, corrupt retrieval, delay responses)
- Baselines: RAGAS, ARES, TruLens component-level metrics

## Technical Stack

### Shared Infrastructure
- **Knowledge graphs**: property graph store (Neo4j or equivalent) + vector index (dense embeddings)
- **LLM backends**: multi-backend support (open-weight + commercial) for reproducibility
- **Observability**: OpenTelemetry GenAI semantic conventions for trace/span logging
- **Simulation**: OpenSeesPy (FEA/structural), SUMO (traffic), domain-specific tools

### Prior Work Foundation
- Brown & Cusati, ESEM 2025: evidence-based beliefs of generative AI tools (SE validation context)
- Cusati & Brown, ICSE-FoSE 2026: knowledge accumulation in SE research — "from papers to progress" (direct PA-AKG precursor)
- djjay-qualifier.pdf: full research proposal for PA-AKG with E1–E4 evaluation framework

## Document Toolchain

### Proposal Preparation
- **Format**: TBD (likely LaTeX or portal submission form)
- **References**: BibTeX bibliography management
- **Version Control**: Git

### Project Infrastructure
- **Repository**: doe-genesis-cfp-2026
- **Documentation**: Memory-bank system
- **Workflow**: Design-first via construction/ folder

## Key Technical Decisions

_To be tracked in `architecturalDecisions.md` as they are made._

## Constraints

- Abstract: 1-page maximum (excluding references)
- Full proposal: 5 pages plus references
- Project duration: 1 year (starting Fall 2026)
- Must align with United States Department of Energy and the executive order

---

**Note:** Update when technical approach and methodology are defined.
