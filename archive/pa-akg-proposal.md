# PA-AKG: Provenance-Aware Agentic Knowledge Graph Systems

**Status:** Archived — reserved for non-Amazon funding initiatives
**Abstract versions:** `abstract/` (v1), `abstract_v2/` (v2, SOA-grounded)
**CFP topics:** Primary: Knowledge Grounding | Secondary: Agentic AI

## Title

Provenance-Aware Agentic Knowledge Graph Systems for Reliable Multi-Source Grounded AI

## Core Idea

Hybrid architecture integrating structured knowledge graphs, multi-source retrieval, and agent orchestration for reliable grounded reasoning with verifiable provenance. Agents dynamically select among retrieval pathways (dense, sparse, structured graph queries, hybrid) based on task context and confidence.

## Key Contributions

1. **Multi-source knowledge grounding** across KGs, relational DBs, scientific literature, and domain-specific document collections
2. **Automated provenance generation and validation layer** producing fine-grained evidence links (span- and entity-level, not just document-level citation)
3. **Validation agents** that monitor retrieval quality and trigger corrective actions when evidence is weak, contradictory, or insufficient
4. **Provenance signals** structured to align with OpenTelemetry GenAI semantic conventions for auditability

## Research Questions

1. How can heterogeneous knowledge sources be unified into a grounding framework supporting both semantic and structured retrieval?
2. How should agent workflows route and validate across retrieval pathways under uncertainty?
3. What mechanisms enable scalable fine-grained provenance generation tied to specific knowledge entities?
4. How does structured KG grounding improve reasoning accuracy, robustness, and efficiency relative to hybrid RAG baselines?

## Technical Approach

- Hybrid KG + vector retrieval architecture with dynamic pathway selection
- Agent orchestration: planner → retriever → validator agents with explicit provenance contracts
- Provenance generation aligned with OpenTelemetry GenAI conventions
- Evaluation: vector-only RAG vs. hybrid structured retrieval vs. GraphRAG vs. PA-AKG
- Case studies: scientific research discovery + engineering decision-support

## Why This Was Not Submitted to Amazon

- PA-AKG shares "Agentic AI" as secondary topic with AKG-E → reviewer overlap risk
- Core idea (hybrid retrieval, KG-RAG) is increasingly productized at Amazon (Bedrock Knowledge Bases)
- Knowledge Grounding is a broadly funded topic with many channels (NSF, DARPA, other industry)
- Better strategic fit: submit to venues where Knowledge Grounding is the primary focus

## Where to Submit

- NSF programs focused on knowledge-intensive AI / information retrieval
- DARPA programs on AI reasoning and knowledge management
- Other industry research programs (Google, Microsoft, Meta) with Knowledge Grounding tracks
- ACL/EMNLP/NAACL workshops on retrieval-augmented generation

## Key Citations

| Citation Key | Paper | Year |
|---|---|---|
| Lewis2020RAG | Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks | 2020 |
| AWSBedrockHybridSearch2024 | Amazon Bedrock Knowledge Bases Hybrid Search | 2024 |
| Edge2024GraphRAG | From Local to Global: A Graph RAG Approach | 2024 |
| Yan2024CRAG | Corrective Retrieval Augmented Generation | 2024 |
| Ji2023HallucinationSurvey | Survey of Hallucination in Natural Language Generation | 2023 |
| OpenAIFunctionCalling2025 | Function Calling Guide | 2025 |
| OpenTelemetryGenAI2024 | Semantic Conventions for Generative AI Systems | 2024 |

## Related Files

- `abstract/main.tex` — v1 abstract (original draft)
- `abstract_v2/main.tex` — v2 abstract (SOA-grounded, final version)
- `abstract_v2/references.bib` — full BibTeX entries
- `abstract_v2/images/architecture-diagram.png` — PA-AKG architecture diagram
- `files/deep-research-report-rai-hybrid-retrieval.md` — SOA deep research on RAG & Graph Retrieval
- `files/deep-research-topics.md` — CFP topic due diligence with PA-AKG fit matrix
- `docs/topic-analysis.html` — interactive topic analysis with PA-AKG as top-ranked proposal
