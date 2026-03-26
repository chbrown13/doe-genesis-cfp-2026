# Technical Context

## Research Methodology

- TBD

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
