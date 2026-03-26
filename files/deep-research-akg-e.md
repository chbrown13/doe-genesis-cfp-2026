# AKG‑E CFP Topic Due Diligence and Industry Practice Review

## Executive summary

**Assumptions (explicit):** You are preparing an abstract for the entity["company","Amazon","e-commerce and cloud"]–entity["organization","Virginia Tech","public university virginia"] CFP, with a **1‑page abstract (references excluded)** and possible **3–4 page proposal**; your AKG‑E research emphasizes **agentic knowledge graphs**, **simulation‑in‑the‑loop / VVUQ**, **KG‑RAG & hybrid retrieval**, **provenance/evidence**, **serving/memory efficiency**, and **construction‑AI / digital twins**. fileciteturn1file12 fileciteturn1file0

**Workflow (including synthesis):** collect CFP subtopic lists → review 2023–2026 primary sources (official docs/whitepapers/industry blogs + original papers) → extract advances/systems/gaps per topic → compare topics by reviewer alignment/novelty/feasibility/Amazon relevance → **synthesize** ranking + topic→research‑area matrix + guidance for the **three AKG‑E abstracts** + citation/BibTeX set + website-update prompt. fileciteturn1file12 fileciteturn1file0

**Recommendation for AKG‑E topic selection (top two):**
- **Primary: AI for Science & Engineering** — best reviewer alignment to “engineering + simulation + domain constraints,” matching your AKG‑E ontology/simulation/constraint validation layers. fileciteturn1file0 fileciteturn1file12  
- **Secondary: Agentic AI** — best alignment to multi-agent orchestration, tool calling, simulation tools as agent-callable interfaces, and emerging **industry tool connectivity standards (MCP)** that make “simulation-as-a-tool” a mainstream pattern. fileciteturn1file0 citeturn1view0turn0search11turn1view3  

**Why MCP is justified to reference (industry practice):**  
MCP is no longer “just an Anthropic idea”; it is explicitly supported as an integration target by **Amazon Bedrock AgentCore Gateway**, which can convert APIs/Lambda/services into **MCP-compatible tools**, and it is supported by the **Microsoft Agent Framework** with security/auditing guidance. That industry uptake makes MCP a legitimate citation for “standardized tool connectivity” in an engineering-agent proposal. citeturn1view0turn1view3turn0search11

```mermaid
flowchart LR
  A[AKG-E] --> B[Ontology layer: engineering KG]
  A --> C[Simulation tools: FEA/PDE/traffic/BIM parsers]
  A --> D[VVUQ + constraint validation]
  C --> E[Tool standards + gateways (e.g., MCP)]
  D --> F[Trustworthy outputs: verified + auditable]
```

## Cross-topic matrices and ranking

### Topic comparison matrix

| Topic | Reviewer alignment to AKG‑E | Novelty headroom | Feasibility (1 year) | Amazon relevance |
|---|---|---|---|---|
| AI for Science & Engineering | **High** | High | Med | High |
| Agentic AI | **High** | Med–High | **High** | **High** |
| Retrieval‑Augmented Inference / Hybrid Retrieval | Med–High | Med–High | **High** | High |
| Knowledge Grounding | Medium | Med–High | **High** | High |
| Agentic Evaluation | Medium | High | Med | High |
| Responsible AI | Medium | Med | Med | High |

This reflects the CFP’s stated topic areas and where AKG‑E’s *core* contributions land (simulation‑in‑loop with constraints and cross-domain engineering). fileciteturn1file12 fileciteturn1file0

### Cross-reference matrix to AKG‑E research areas

Score: 0 weak, 1 partial, 2 strong, 3 best fit.

| Topic → / AKG‑E areas ↓ | Agentic KGs | KG‑RAG / hybrid retrieval | Provenance / evidence | Memory disaggregation / serving | Construction‑AI / digital twins |
|---|---:|---:|---:|---:|---:|
| AI for Science & Engineering | 3 | 1 | 2 | 2 | 3 |
| Agentic AI | 2 | 1 | 2 | 2 | 2 |
| Hybrid Retrieval | 1 | 3 | 1 | 2 | 2 |
| Knowledge Grounding | 2 | 3 | 2 | 1 | 2 |
| Agentic Evaluation | 1 | 1 | 3 | 2 | 1 |
| Responsible AI | 1 | 1 | 3 | 2 | 1 |

**Synthesis:** For AKG‑E, pick the bucket that naturally routes you to the right reviewers: **AI for Science & Engineering (primary)** + **Agentic AI (secondary)**. Use the other topics as *supporting claims* and optional proposal sections (evaluation plan, hybrid retrieval, tool governance). fileciteturn1file0 fileciteturn1file12

## Topic reports

### AI for Science and Engineering

**Executive summary:** AKG‑E is fundamentally a science/engineering acceleration framework: it couples **structured domain knowledge + simulation + validation (VVUQ)**. This aligns cleanly with the CFP’s “AI‑accelerated science and engineering” intent. fileciteturn1file0 fileciteturn1file12

**Key subtopics (6–10):** simulation‑in‑the‑loop agents; FEA/PDE tool integration; constraint satisfaction (physics + regulatory); VVUQ for agent outputs; digital twins + closed-loop control; uncertainty propagation; cross-domain ontology modularity; reproducibility + benchmarks; human-in-the-loop verification.

**Recent advances (2023–2026; primary sources):**
- **LLM→simulation automation** is emerging as a concrete research direction: MCP‑SIM is a memory‑coordinated multi‑agent framework that constructs/executes finite element simulations from natural language and evaluates physical convergence and interpretability across tasks. citeturn3search6turn1view4  
- Construction digital twins are increasingly studied as decision-support systems, with identified needs around human interfaces and workflow integration—useful motivation for AKG‑E’s “trust + validation” thesis. citeturn3search0  
- LLM multi-agent tooling is being applied to structural engineering workflows like finite element modeling, indicating a growing body of “engineering agent” baselines to compare against. citeturn3search2  

**Representative systems / provider features (industry practice):**
- Agent platforms are converging on “tools + memory + governance + observability” primitives (useful for deploying simulation tools safely at scale), e.g., AgentCore concepts of tool gateways and memory observability signals. citeturn1view2turn1view1turn4search1  

**Open gaps / risks:** validation standards for AI-generated engineering artifacts are immature; unsafe tool invocation and overconfident outputs remain key hazards; cross-domain generalization requires careful ontology modularity rather than “one giant schema.” citeturn3search6turn3search2

**Fundable research directions aligned to AKG‑E (3–5):**
- **AKG‑E VVUQ harness:** formalize verification + validation for agent-generated designs; report uncertainty and safety margins.
- **Simulation tool adapters:** wrap FEA/PDE/traffic/BIM parsers into callable tools with typed I/O and constraints.
- **Constraint-aware planners:** planners that must satisfy domain constraints (codes/physics) before emitting outputs.
- **Construction digital twin pilot:** material takeoff + schedule reasoning + simulation validation loop in one workflow.

**Likely reviewer questions + concise pre-answers:**
- *What engineering proof point will you deliver?* → pick 1–2 domains (construction + transportation) with measurable metrics (constraint violations, accuracy, latency).
- *How do you prevent “LLM hallucinated physics”?* → enforce simulation‑in‑loop + constraints + VVUQ gates.
- *Is this too broad?* → emphasize domain‑agnostic architecture + two carefully scoped pilots.

**Title variants:**
- “AKG‑E: Simulation‑Validated Agentic Knowledge Graphs for Engineering”
- “VVUQ‑Grounded Agents for Construction and Transportation Digital Twins”
- “Constraint‑Verified LLM Agents for Engineering Decision Support”

**Recommended citations (3–5 keys):** MCP‑SIM (2026), construction digital twins (2025), multi‑agent FEA automation (2025). citeturn3search6turn3search0turn3search2

---

### Agentic AI

**Executive summary:** Agentic AI is the best secondary because AKG‑E depends on robust orchestration across retrieval, tool calls, simulation, and validation. Industry is standardizing the “tools layer” via gateways and protocols (notably MCP), which strengthens AKG‑E’s feasibility argument. fileciteturn1file0 citeturn1view0turn0search11turn1view3

**CFP anchor subtopics (examples):** multi-agent systems/orchestration; agent-environment interaction; post-deploy improvement; deep research/coding/cybersecurity applications. fileciteturn1file12

**Key subtopics (6–10):** orchestration patterns (planner–executor–validator); tool discovery/routing; multi-agent communication; long-running sessions; memory & state; simulation as a tool; governance/policies around tools; observability and traceability.

**Recent advances / industry practice (2023–2026):**
- **Tool calling** is explicitly defined as a multi-step application ↔ model loop in official API guidance (critical for describing simulation calls). citeturn4search0  
- **MCP** is documented as an open standard for secure two-way tool/data connections, and is treated as a practical interoperability layer. citeturn0search11  
- **AgentCore Gateway** can convert APIs/Lambda/services into MCP-compatible tools and supports tool discovery (semantic search), plus managed auth—directly relevant to “simulation tool registries” for AKG‑E. citeturn1view0  

**Representative systems / provider features:**
- Agent platforms emphasized by AWS: build/deploy/operate agents with tools, memory, monitoring; gateway + policy + observability exist as distinct services. citeturn4search1turn1view2turn4search7  

**Open gaps / risks:** tool misuse and prompt injection; wrong tool selection/parameters; need for principled fallback and validation; ensuring simulation results don’t leak sensitive data into prompts. citeturn1view3turn1view0  

**Fundable directions (3–5):**
- **Simulation-tool registry via MCP:** publish engineering tools (FEniCS, BIM parsers, microsims) as MCP tools.
- **Validator agents:** automated checks on simulation convergence + constraint compliance before response emission.
- **Tool governance:** define tool policies outside agent code (who can call what, with what bounds).
- **Observability-first agents:** structured spans linking tool calls ↔ memory ↔ outputs for auditability.

**Reviewer Qs + pre-answers:**
- *Is MCP necessary?* → it’s a pragmatic interoperability choice; both AWS gateways and Microsoft agents support it.
- *How do you prevent tool abuse?* → policy enforcement + least-privilege + bounded input validation.
- *How do you evaluate agent quality?* → domain metrics + VVUQ + reproducible benchmarks.

**Title variants:**
- “Tool‑Standardized Engineering Agents with Simulation‑in‑the‑Loop Validation”
- “MCP‑Connected Engineering Toolchains for Multi‑Agent LLM Systems”
- “Agentic Orchestration for Verified Simulation and Constraint Reasoning”

**Recommended citations (3–5 keys):** MCP intro, AgentCore Gateway (MCP tools), Microsoft MCP integration, OpenAI function calling. citeturn0search11turn1view0turn1view3turn4search0

---

### Retrieval‑Augmented Inference and Hybrid Retrieval

**Executive summary:** Even for simulation-heavy AKG‑E, retrieval is a practical necessity: engineering workflows require grounding in **codes, specs, BIM artifacts, sensor logs, past project data**, and simulation outputs. Industry practice strongly favors **hybrid lexical + semantic retrieval** and retrieval as a callable tool. citeturn2search0turn2search1

**Key subtopics (6–10):** sparse+dense hybrid retrieval; metadata filtering; doc-to-graph indexing; tool-exposed retrieval; reranking; retrieval quality evaluation; structured retrieval (SQL/graph); multimodal retrieval for drawings; caching and cost control.

**Recent advances / industry practice (2023–2026):**
- **Hybrid search** is productized in Bedrock Knowledge Bases and explicitly described as combining semantic + text search to improve relevance for keyword-heavy queries. citeturn2search4turn2search0  
- **File search tools** now explicitly implement semantic + keyword search over uploaded corpora (tool-exposed retrieval). citeturn2search1  
- Robustness research like **CRAG** formalizes retrieval evaluation and corrective actions when retrieval goes wrong (useful for “engineering spec mismatch” scenarios). citeturn2search3  

**Representative systems/provider features:** Bedrock Knowledge Bases hybrid retrieval; tool-based file search. citeturn2search4turn2search1

**Open gaps / risks:** retrieval failures can silently degrade correctness; engineering documents have dense tables/figures; provenance granularity remains hard; prompt injection via retrieved tool context. citeturn2search3turn1view3  

**Fundable directions (3–5):**
- **Engineering hybrid retrieval baselines:** sparse+dense+rering for specs/codes/BIM metadata.
- **Retrieval evaluator for engineering:** detect stale/irrelevant specs; trigger alternative retrieval or simulation checks.
- **Graph retrieval for design artifacts:** build entity graphs over BOMs, components, constraints.
- **Multimodal retrieval:** drawings + IFC/BIM parsing with retrieval across text+vision.

**Reviewer Qs + pre-answers:**
- *Why not rely on long context?* → retrieval provides freshness, precision, and cost control; engineering demands exactness.
- *How do you evaluate retrieval?* → gold-labeled evidence sets + retrieval recall/precision + downstream constraint violation rate.
- *How does retrieval connect to simulation?* → retrieved params/constraints seed simulation tools; results re-ingested as evidence.

**Title variants:**
- “Hybrid Retrieval for Engineering Agents: From Specs to Simulation”
- “Corrective Hybrid Retrieval Pipelines for Safety‑Critical Engineering Workflows”
- “Tool‑Exposed Retrieval for Digital Twin Decision Support”

**Recommended citations (3–5 keys):** Bedrock hybrid search, OpenAI file search, CRAG. citeturn2search4turn2search1turn2search3

---

### Knowledge Grounding

**Executive summary:** This topic overlaps heavily with hybrid retrieval, but is broader (fusion across heterogeneous sources). For AKG‑E, ground truth comes not only from documents but from **simulation outputs** and **structured design artifacts**, so grounding should be framed as “evidence from tools + sources,” not only RAG. fileciteturn1file0 citeturn2search1turn2search0

**CFP anchor examples:** memory-augmented systems; multimodal retrieval across heterogeneous sources; fusion of knowledge sources; improved LLM↔external knowledge interaction. fileciteturn1file12

**Key subtopics (6–10):** heterogeneous source fusion; grounding via structured artifacts (BIM/BOM); tool outputs as evidence; multimodal grounding; provenance/citations; conflict detection; domain ontologies; grounding-aware planning.

**Recent advances / practice:** tool-grounding (Search grounding; file search tools) indicates providers are pushing “grounding as a first-class capability,” which can be analogized to grounding on simulation evidence. citeturn2search1turn7search3  

**Representative systems/provider features:** “grounding with search” patterns plus enterprise grounding tools; in AKG‑E, replace “search” with “simulation and structured engineering data.” citeturn7search3turn1view0  

**Open gaps / risks:** fusion under contradictions; multimodal artifacts; proof obligations for engineering claims; provenance for tool-generated evidence. citeturn1view1turn3search6

**Fundable directions (3–5):**
- **Evidence graph unifying docs + simulation artifacts** (structured provenance linking inputs→sim→outputs).
- **Grounding-aware constraint checks** that require evidence for every parameter/value used.
- **Ontology plugins** for construction/transportation/thermal domains (shared interface, domain-specific rules).

**Reviewer Qs + pre-answers:**
- *Is this just knowledge grounding rebranded?* → no: engineering grounding includes simulation truth + constraints + VVUQ.
- *How will grounding be verified?* → simulation convergence + constraint satisfaction + evidence links.
- *What’s the minimum viable scope?* → 2 domains, shared ontology interface, shared validation harness.

**Title variants:**
- “Grounding Engineering Agents in Simulation Evidence and Structured Design Artifacts”
- “From RAG to RAV: Retrieval‑and‑Validation for Engineering Digital Twins”
- “Multi‑Source Grounding with Ontologies, Tools, and Verification”

**Recommended citations (3–5 keys):** file search (hybrid), Bedrock hybrid search, MCP-SIM (simulation evidence). citeturn2search1turn2search4turn3search6

---

### Agentic Evaluation

**Executive summary:** For AKG‑E, evaluation is not “answer accuracy” but **engineering validity**. The strongest move is to position VVUQ and constraint validation as the evaluation core, while borrowing agent benchmarks for tool-use reliability. fileciteturn1file1 fileciteturn1file2

**CFP anchor examples:** new benchmarks; robust evaluation methodologies for generative systems including agents. fileciteturn1file12

**Key subtopics (6–10):** tool-use benchmarks; simulation validity metrics; constraint violation scoring; uncertainty quantification; reproducibility harness; multi-agent coordination reliability; cost/latency metrics; audit logs.

**Recent advances / practice:**
- AgentBench and GAIA exemplify interactive agent evaluation; they can serve as scaffolding patterns, but AKG‑E needs domain-specific “validity” metrics. citeturn6view7turn6view8  
- A key additional signal for AKG‑E is **tool + memory observability**: AgentCore provides structured spans linking memory operations and events, supporting rigorous evaluation and debugging. citeturn1view1turn1view2  

**Representative systems/provider features:** agent benchmarks (AgentBench/GAIA); observability and memory spans (AgentCore). citeturn6view7turn1view1

**Open gaps / risks:** mismatch between offline eval and deployment; measuring “engineering correctness” requires domain truth; uncertainty reporting can be gamed without proper harnessing. citeturn3search6turn1view1

**Fundable directions (3–5):**
- **AKG‑E VVUQ benchmark suite:** standardized tasks (frame FEA, heat diffusion, traffic flow) with ground-truth checks.
- **Failure mode taxonomy**: wrong boundary conditions, non-convergent sims, constraint contradictions.
- **Observability-first evaluation**: spans/traces that allow replay and comparison across agent versions.

**Reviewer Qs + pre-answers:**
- *How is this evaluated rigorously?* → simulation convergence + constraint metrics + uncertainty bounds (VVUQ framing).
- *How will you compare to baselines?* → prompt-only vs RAG vs tool+validation pipeline on identical tasks.
- *Is the evaluation reusable?* → yes: domain-agnostic harness with domain plug-ins.

**Title variants:**
- “VVUQ as Agent Evaluation: Measuring Validity in Tool‑Using Engineering Agents”
- “Benchmarks for Simulation‑Integrated Agent Reliability”
- “Evaluating Engineering Agents via Constraints, Convergence, and Uncertainty”

**Recommended citations (3–5 keys):** AgentBench, GAIA, AgentCore memory spans/observability. citeturn6view7turn6view8turn1view1

---

### Responsible AI

**Executive summary:** Responsible AI is not the primary “home” topic for AKG‑E, but it is critical operationally: simulation tools and data can be sensitive; tool misuse is a real risk; and governance is increasingly part of agent platforms. citeturn4search2turn4search7

**CFP anchor examples:** red teaming; robustness to jailbreaks; responsible agentic AI; frontier risks; cultural alignment. fileciteturn1file12

**Key subtopics (6–10):** tool governance and least-privilege; prompt injection defenses; policy-as-code; overrefusal vs safety; secure sandboxing; audit logging; data retention; safety evaluation; compliance.

**Recent advances / practice:**
- Bedrock Guardrails provides configurable safeguards and privacy controls for genAI apps (baseline safety layer). citeturn4search2  
- Agent tool governance is moving “outside agent code”: AgentCore **Policy** converts natural language to **Cedar** and intercepts agent-tool traffic for centralized controls. That is directly relevant to “safe simulation tool invocation.” citeturn4search7  
- Constitutional Classifiers (and next-generation variants) represent production-focused jailbreak robustness research and quantify deployment tradeoffs. citeturn4search3turn4search6  

**Representative systems/provider features:** Guardrails + centralized tool policies + MCP security considerations. citeturn4search2turn4search7turn1view3

**Open gaps / risks:** tool supply-chain issues; injection via retrieved code/specs; ensuring simulation environments are sandboxed; balancing safety with usability/latency. citeturn1view3turn4search7  

**Fundable directions (3–5):**
- **Policy-bound simulation tools:** enforce parameter bounds, prohibitions, and approvals for high-risk actions.
- **Prompt-injection testbed** for engineering-spec retrieval and BIM documents.
- **Audit-grade traces**: link every output to tool calls and evidence for accountability.

**Reviewer Qs + pre-answers:**
- *Why include safety if not the primary topic?* → because engineering tools are sensitive; governance is required for deployment.
- *How do you prevent destructive tool actions?* → central policy + bounded tool APIs + sandboxing.
- *How do you handle data privacy?* → minimize context exposure; store sensitive artifacts outside prompts.

**Title variants:**
- “Governed Engineering Agents: Policy‑Bound Simulation Tools with Audit Trails”
- “Safe Tool‑Using Engineering Agents via Centralized Policy and Validation”
- “Responsible Simulation‑Integrated Agents for Digital Twins”

**Recommended citations (3–5 keys):** Bedrock Guardrails, AgentCore Policy, MCP security/auditing guidance via Microsoft MCP article, Constitutional Classifiers. citeturn4search2turn4search7turn1view3turn4search6

## Recommendations on the three AKG‑E abstracts

You provided three AKG‑E variants:

- **Across domains** (broad, domain-agnostic): fileciteturn1file0  
- **Construction + transportation with VVUQ framing**: fileciteturn1file1  
- **Construction-only with VVUQ**: fileciteturn1file2  

### Which one to prioritize for submission

**Best default to submit:** the **Construction + Transportation (VVUQ)** version. It balances (i) cross-domain generality (AKG‑E as a framework) with (ii) concrete evaluation and two pilots (mitigates “too broad” reviewer concerns), while staying aligned to the primary topic **AI for Science & Engineering**. fileciteturn1file1 fileciteturn1file12

**When to submit Across‑Domains instead:** only if you can credibly commit to (and concisely state) a *shared evaluation harness* that makes cross-domain claims falsifiable; otherwise it risks reading as “vision-only.” fileciteturn1file0

**When to submit Construction‑only instead:** if you anticipate domain reviewers who prefer depth over breadth (e.g., construction faculty), or if schedule/time makes a two-domain validation implausible. fileciteturn1file2

### High‑leverage edits (industry practice + citations)

1. **Add a 1–2 sentence “industry integration” justification**: cite that modern agent platforms convert APIs into MCP tools and provide tool discovery + auth + observability, which you’ll leverage for simulation tools (FEniCS/FEM/BIM parsers). citeturn1view0turn1view2turn1view3turn0search11  
2. **Replace (or augment) bio/materials “motivation” with engineering-agent evidence**: cite MCP‑SIM (simulation from prompts) and one structural engineering agent automation paper to show this is an emerging engineering practice, not only an analogy to biology/materials. citeturn3search6turn3search2  
3. **Make evaluation feel non-negotiable**: state that outputs are only released after passing convergence + constraint checks, and uncertainty is reported (VVUQ). Pair with a citation that digital twins in construction emphasize decision support needs (human trust + workflow integration). citeturn3search0turn1view4  

## Image and diagram suggestions

- **AKG‑E layered architecture** (ontology → tools/sim → VVUQ/constraints) with domain plug-in boxes for construction/transportation/thermal. fileciteturn1file0  
- **Tool connectivity diagram**: simulation tools registered as MCP tools via a gateway; include policy intercept + traces/spans. citeturn1view0turn4search7turn1view1  
- **Evaluation “gate” diagram**: generation → retrieve/plan → simulate → verify → only then “deliver.” citeturn1view4  

## Claude prompt to update a website from this Markdown file

```markdown
You are working inside our website Git repo.

Goal:
- Publish the attached Markdown report as a new page.
- Ensure Markdown tables render and Mermaid blocks render.
- Add the page to site navigation.
- Do NOT change technical content except minimal formatting required by the site.

Assumptions:
- The site supports Markdown pages (docs/ or content/).
- Mermaid support may require enabling a plugin.

Tasks:
1) Create/update: docs/reports/akge-topic-due-diligence.md
   Add frontmatter (adjust if our site uses different keys):
   ---
   title: "AKG-E CFP Topic Due Diligence"
   description: "Six-topic deep research review for selecting primary/secondary CFP categories for AKG-E."
   slug: /reports/akge-topic-due-diligence
   ---

2) Ensure Mermaid rendering:
   - If Docusaurus: enable @docusaurus/theme-mermaid and markdownMermaid.
   - If MkDocs: enable pymdownx.superfences with mermaid fences.
   - If Next.js: add a Mermaid MDX/remark plugin consistent with our stack.

3) Add nav entry:
   - Put this under “Reports” in the sidebar/nav.

4) Validate layout:
   - Ensure wide tables are readable (add safe horizontal scroll wrapper if supported).

5) Output a short PR summary:
   - List files changed + what/why.

Here is the Markdown to publish:
[PASTE THE FULL REPORT MARKDOWN HERE]
```

## Ready-to-paste BibTeX block for recommended citations

```bibtex
@misc{AnthropicMCP2024,
  author       = {{Anthropic}},
  title        = {Introducing the Model Context Protocol},
  year         = {2024},
  month        = nov,
  howpublished = {Anthropic News},
  url          = {https://www.anthropic.com/news/model-context-protocol},
  note         = {Accessed 2026-03-15}
}

@misc{AWSAgentCoreGatewayMCP,
  author       = {{Amazon Web Services}},
  title        = {Amazon Bedrock AgentCore Gateway: Securely connect tools and other resources to your Gateway},
  year         = {2025},
  howpublished = {AWS Documentation},
  url          = {https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/gateway.html},
  note         = {Accessed 2026-03-15}
}

@misc{MicrosoftAgentFrameworkMCP2026,
  author       = {{Microsoft}},
  title        = {Microsoft Agent Framework: Using MCP tools with Agents},
  year         = {2026},
  month        = feb,
  howpublished = {Microsoft Learn},
  url          = {https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools},
  note         = {Accessed 2026-03-15}
}

@misc{OpenAIFunctionCalling2025,
  author       = {{OpenAI}},
  title        = {Function calling (tool calling flow)},
  year         = {2025},
  month        = aug,
  howpublished = {OpenAI Developer Documentation},
  url          = {https://developers.openai.com/api/docs/guides/function-calling/},
  note         = {Accessed 2026-03-15}
}

@misc{AWSKBHybridSearchWhatsNew2024,
  author       = {{Amazon Web Services}},
  title        = {Knowledge Bases for Amazon Bedrock now supports hybrid search},
  year         = {2024},
  month        = mar,
  howpublished = {AWS What's New},
  url          = {https://aws.amazon.com/about-aws/whats-new/2024/03/knowledge-bases-amazon-bedrock-hybrid-search/},
  note         = {Accessed 2026-03-15}
}

@misc{OpenAIFileSearchTool2025,
  author       = {{OpenAI}},
  title        = {File search (Responses API tool): semantic and keyword search over uploaded corpora},
  year         = {2025},
  howpublished = {OpenAI Developer Documentation},
  url          = {https://developers.openai.com/api/docs/guides/tools-file-search/},
  note         = {Accessed 2026-03-15}
}

@article{Yan2024CRAG,
  author  = {Yan, Shi-Qi and Gu, Jia-Chen and Zhu, Yun and Ling, Zhen-Hua},
  title   = {Corrective Retrieval Augmented Generation},
  year    = {2024},
  journal = {arXiv},
  url     = {https://arxiv.org/abs/2401.15884},
  note    = {Accessed 2026-03-15}
}

@article{Edge2024GraphRAG,
  author  = {Edge, Darren and others},
  title   = {From Local to Global: A Graph RAG Approach to Query-Focused Summarization},
  year    = {2024},
  journal = {arXiv},
  url     = {https://arxiv.org/abs/2404.16130},
  note    = {Accessed 2026-03-15}
}

@article{Park2026MCPSIM,
  author  = {Park, D. and others},
  title   = {A self-correcting multi-agent LLM framework for language-based physics simulation and explanation},
  year    = {2026},
  journal = {npj Artificial Intelligence},
  url     = {https://www.nature.com/articles/s44387-025-00057-z},
  note    = {Accessed 2026-03-15}
}

@article{LLMAgentsFEM2025,
  author  = {Xia, C. S. and others},
  title   = {A Lightweight Large Language Model-Based Multi-Agent System to Automate Finite Element Modeling of 2D Frames},
  year    = {2025},
  journal = {arXiv},
  url     = {https://arxiv.org/html/2510.05414v1},
  note    = {Accessed 2026-03-15}
}

@article{Soman2025ConstructionDT,
  author  = {Soman, R. K. and others},
  title   = {Digital twin construction with a focus on human interaction and decision-making},
  year    = {2025},
  journal = {Automation in Construction},
  url     = {https://www.sciencedirect.com/science/article/pii/S0926580524006605},
  note    = {Accessed 2026-03-15}
}

@misc{AWSBedrockGuardrailsDocs,
  author       = {{Amazon Web Services}},
  title        = {Detect and filter harmful content by using Amazon Bedrock Guardrails},
  year         = {2025},
  howpublished = {AWS Documentation},
  url          = {https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html},
  note         = {Accessed 2026-03-15}
}

@misc{AWSAgentCorePolicyGA2026,
  author       = {{Amazon Web Services}},
  title        = {Policy in Amazon Bedrock AgentCore is now generally available},
  year         = {2026},
  month        = mar,
  howpublished = {AWS What's New},
  url          = {https://aws.amazon.com/about-aws/whats-new/2026/03/policy-amazon-bedrock-agentcore-generally-available/},
  note         = {Accessed 2026-03-15}
}

@misc{AnthropicConstitutionalClassifiers2025,
  author       = {{Anthropic}},
  title        = {Constitutional Classifiers: Defending against universal jailbreaks},
  year         = {2025},
  month        = feb,
  howpublished = {Anthropic Research},
  url          = {https://www.anthropic.com/research/constitutional-classifiers},
  note         = {Accessed 2026-03-15}
}
```