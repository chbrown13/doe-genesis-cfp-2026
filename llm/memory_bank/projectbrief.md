# Project Brief — DOE Genesis Mission CFP 2026

## One-line description

A research proposal repository preparing and submitting PA-AKG (Provenance-Aware Agentic Knowledge Graphs) to the U.S. Department of Energy's *Genesis Mission: Transforming Science and Energy with AI* request for applications (RFA `DE-FOA-0003612`).

## Purpose

Produce a competitive full-proposal submission for focus area **18E — HPC Code Curation, Translation, and Development: Trustworthy AI for Scientific Software**, with fallback participation in focus areas 11C and 19B. Secure 1-year research funding starting 2026-07-01 to build PA-AKG as foundational infrastructure for trustworthy AI-assisted scientific software development at DOE national laboratories.

## Research problem and approach

Current agentic AI systems coordinating multiple agents and retrieving documentation to ground code recommendations cannot provide the **trustworthiness guarantees** that HPC scientific software requires. They may suggest transformations but cannot trace each recommendation to the specific performance benchmarks, numerical analyses, or validation results that justify it. In DOE scientific software, numerically incorrect changes can silently invalidate entire simulation campaigns.

PA-AKG addresses this gap with a three-layer architecture:

1. **Knowledge Representation** — persistent hybrid property-graph + vector-index encoding algorithms, numerical methods, code components, benchmarks, validation results, and development decisions as first-class entities linked by typed semantic relations.
2. **Automation & Extraction** — structured prompting produces claim–evidence pairs; span-level alignment ties each claim to character-level source spans; canonicalization auditing normalizes and deduplicates entity references.
3. **Agentic Orchestration** — role-specific agents (ranking, continuation, evaluation, synthesis) operating under a **provenance inheritance constraint** enforced at every agent handoff.

The key invariant: provenance enforcement is **architectural**, not post-hoc. Confirmed decisions are written back to the KG with explicit evidence chains, accumulating an auditable development history that future agents build upon.

## Target users and beneficiaries

- **Primary**: HPC scientific software developers at DOE national laboratories (Sandia, Argonne, Oak Ridge, Livermore) performing code curation, translation across hardware targets, and numerical-method modernization.
- **Secondary**: Software engineering researchers studying evidence-based AI assistance, AI practitioners building trustworthy code-assistance tools, and DOE program managers needing audit trails for AI-assisted research outputs.

## Team

- **PI**: Dr. Chris Brown (Computer Science, Virginia Tech) — project execution lead
- **Co-PI**: Dr. Xuan Wang (Computer Science, Virginia Tech) — evaluation methodology, knowledge retrieval and extraction, benchmark design
- **Co-PI**: Dr. Scott T. Steinmetz (Sandia National Labs) — HPC validation corpus, trust in AI systems, Sandia-side deployment
- **GRA**: Jason Cusati (Computer Science, Virginia Tech) — design and implementation of the PA-AKG infrastructure, daily proxy for sign-off relay

## Scope — in scope

- Pre-proposal abstracts for 11C, 18E, 19B (submitted 2026-03-27)
- Full proposal for 18E (due 2026-04-28) with five-page narrative + references
- LaTeX manuscript authoring using the `files/proposalnsf` document class
- Reference management via BibTeX
- Reviewer-feedback incorporation with explicit traceability from comments to edits
- Design-first construction workflow (see `systemPatterns.md`)
- GitHub Pages dashboard at `docs/index.html` for stakeholder visibility
- Memory-bank documentation (this system)

## Scope — explicitly out of scope

- Actual PA-AKG research execution (that begins 2026-07-01 if funded, in a separate execution repository)
- Software implementation of the PA-AKG architecture
- Data collection beyond reference-paper curation for the calibration studies
- Budget and cost-share negotiation (handled separately)
- Appendix 2 computing-resource requests
- Editing the frozen pre-proposal abstracts (`abstract_11C/`, `abstract_18E/`, `abstract_19B/`) after 2026-03-27 submission

## Key constraints

- **Pre-proposal**: 1 page maximum (excluding references) — SUBMITTED 2026-03-27
- **Full proposal**: 5 pages plus references — DUE 2026-04-28
- **Project duration**: 1 year (2026-07-01 through 2027-06-30)
- **Eligibility**: Full-time tenure-track, research-track, and teaching faculty at VT eligible as PIs
- **Alignment**: Must address the Genesis Mission National Science and Technology Challenges and Executive Order 14363 on AI-accelerated scientific discovery
- **DOE audience**: Merit review against five DOE criteria, with Criterion 1 (Technical Merit and Impact) the most heavily weighted
- **Traceability requirement** (introduced v2 2026-04-09): every reviewer-driven LaTeX edit carries an inline `% [RF-<n>]` comment tag for grep-auditable coverage

## Key milestones

| Date | Milestone | Status |
|---|---|---|
| 2026-03-05 | Project initialization | Complete |
| 2026-03-27 | Pre-proposal submissions (11C, 18E, 19B) | Complete |
| 2026-04-01 | Notification to submit full proposals (18E #1/2 ranking; invited) | Complete |
| 2026-04-09 | Sandia meeting + v2 reviewer-feedback incorporation | In progress |
| 2026-04-10 | Page-budget session | Pending |
| 2026-04-28 | Full proposal due | Pending |
| ~2026-06 | DOE Genesis award decision | Pending |
| 2026-07-01 | Projects begin (if funded) | Pending |
