# Website Restructure Design

_Created: 2026-03-14_

## Overview

The GitHub Pages site was restructured from a single-page dashboard to a multi-page site with dedicated pages for each proposal and analysis artifact. All pages share a consistent navigation bar and dark-theme styling (VT maroon + Amazon orange).

## Site Map

```
docs/
├── index.html                  # Dashboard — main landing page
├── favicon.svg                 # Site favicon
├── proposal-pakg.html          # PA-AKG dedicated proposal page
├── proposal-akge.html          # AKG-E dedicated proposal page
├── proposal-svf.html           # SVF dedicated proposal page
├── downloads.html              # Downloads page (PDFs, abstracts)
├── devils-advocate.html        # Devil's advocate analysis
├── submission-strategy.html    # Submission strategy analysis
├── topic-analysis.html         # Full topic analysis
├── deep-research-report.html   # Deep research report (RAG & Graph SOA)
├── pa-akg-archive.html         # PA-AKG archive (earlier versions)
├── strategy-notes.md           # Strategy notes source
├── abstract.pdf                # Abstract v1 (PA-AKG)
├── abstract_v2.pdf             # Abstract v2 (PA-AKG, SOA-grounded)
├── abstract_v3.pdf             # Abstract v3 (SVF)
├── abstract_v4.pdf             # Abstract v4 (AKG-E)
└── cfp-instructions.pdf        # CFP instructions reference
```

## Page Descriptions

### Dashboard (index.html)

Main landing page. Contains:

- **Header**: Project title, subtitle, partner logos area
- **Ranked proposal cards**: Three cards ordered by ranking (#1 PA-AKG, #2 AKG-E, #3 SVF), each showing:
  - Rank badge and proposal name
  - Primary and secondary CFP topics
  - Current status
  - Link to dedicated proposal page
  - Link to download PDF
- **Analysis section**: Links to devil's advocate, submission strategy, topic analysis
- **Timeline**: Key dates and milestones
- **Navigation bar**: Shared across all pages

### Dedicated Proposal Pages

Each proposal has its own page with detailed content:

- **proposal-pakg.html** — PA-AKG: Provenance-Aware Agentic Knowledge Graph Systems
  - Full abstract text, architecture details, key references
  - Topics: Knowledge Grounding (primary) + Agentic AI (secondary)

- **proposal-akge.html** — AKG-E: Agentic Knowledge Graphs for Engineering
  - Full abstract text, application domains, VVUQ details
  - Topics: AI for Science & Engineering (primary) + Agentic AI (secondary)

- **proposal-svf.html** — SVF: Structured Validation Framework
  - Full abstract text, evaluation dimensions, benchmark design
  - Topics: Agentic Evaluation (primary) + Responsible AI (secondary)

### Downloads Page (downloads.html)

Central location for all downloadable artifacts:

- Abstract PDFs (v1-v4)
- CFP instructions PDF
- Links to all analysis pages

### Analysis Pages

- **devils-advocate.html** — Honest strengths/weaknesses analysis of each proposal, ranking rationale
- **submission-strategy.html** — Strategy analysis for which proposals to submit, topic overlap concerns, reviewer pool considerations
- **topic-analysis.html** — Full CFP topic analysis surfaced for advisor review
- **deep-research-report.html** — Deep research report on RAG & Graph Retrieval SOA (2023-2026)

### Archive Pages

- **pa-akg-archive.html** — Archive of earlier PA-AKG versions (v1, v2 iterations)

## Navigation Bar

Shared across all pages. Links:

- Dashboard (index.html)
- PA-AKG (proposal-pakg.html)
- AKG-E (proposal-akge.html)
- SVF (proposal-svf.html)
- Downloads (downloads.html)
- Analysis dropdown or links:
  - Devil's Advocate
  - Submission Strategy
  - Topic Analysis
  - Deep Research Report

## Design Decisions

- **Dark theme**: Consistent with VT maroon (#861F41) and Amazon orange (#FF9900) branding
- **Ranked cards on dashboard**: Provides at-a-glance view of proposal status and priority
- **Dedicated pages**: Each proposal gets its own page to avoid a single massive dashboard
- **Shared nav bar**: Ensures easy navigation between all pages
- **Static HTML**: No build step needed; pages served directly via GitHub Pages
