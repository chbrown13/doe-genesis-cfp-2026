---
title: "18E — Candidate DOE Codes for PA-AKG Evaluation"
layout: default
---

# 18E — Candidate DOE Codes for PA-AKG Evaluation

**Focus Area:** 18E — Trustworthy AI for Scientific Software
**Context:** Selecting 1–3 concrete DOE codes to anchor the PA-AKG evaluation in the Full Proposal (due 2026-04-28). Selection is filtered by three constraints: (1) access via Co-PI Scott T. Steinmetz (Sandia), (2) fit with the PA-AKG provenance evaluation plan (E1–E4), and (3) availability of rich benchmark/translation history for AI agents to reason over.

---

## Selection Criteria

A candidate code is a strong anchor for PA-AKG if it satisfies the following:

1. **Sandia access.** Steinmetz can provide the validation corpus, performance logs, and domain expertise. Avoids data-agreement delays.
2. **Open-source + public provenance.** Git history, issue tracker, and published benchmarks are ingestible into the knowledge graph without export-control friction.
3. **Translation / portability pressure.** The code has a documented history of being ported across CPU/GPU/accelerator targets — exactly the workflow PA-AKG must make trustworthy.
4. **Numerical validation history.** Test suites, regression corpora, or published validation studies exist so that span-level evidence alignment (E1) has meaningful ground truth.
5. **Scope control.** The code (or a well-defined subset of it) is small enough for a 12-month evaluation but complex enough to exercise the full provenance chain.

---

## Recommended Anchor Set (Primary → Tertiary)

The three codes below form a natural **library → numerical framework → application** progression. Each layer exercises a different class of AI-assisted transformation, and all three are Sandia-originated or Sandia-co-developed, so Steinmetz's role becomes concrete.

### 1. **Kokkos** *(Primary anchor — performance-portability layer)*

- **What it is.** C++ performance-portability programming model. Lets a single source base target CPU, NVIDIA GPU, AMD GPU, and Intel GPU backends.
- **Sandia role.** Led by Sandia's Center for Computing Research; foundational component of the DOE Exascale Computing Project (ECP).
- **Why it fits PA-AKG.** Kokkos is literally a *translation layer* — it exists because scientific software must be re-expressed across hardware targets. AI-suggested refactors into Kokkos idioms (view allocation, execution/memory spaces, parallel dispatch) are high-value and high-risk: a wrong execution space kills performance silently. Perfect fit for span-level evidence alignment (E1) and reproducibility (E3).
- **Evaluation handle.** Use public Kokkos tutorials and kernels as a controlled corpus; use a Sandia-internal Kokkos port history (via Steinmetz) for the longitudinal stability axis (E4).
- **Risk.** Kokkos is a library, not a full application — need to pair it with a client code to show end-to-end impact.

### 2. **Trilinos** *(Secondary anchor — numerical framework)*

- **What it is.** Large collection of parallel numerical solver packages (linear/nonlinear solvers, preconditioners, discretizations, graph partitioners). Open source, BSD.
- **Sandia role.** Sandia-originated and Sandia-maintained. One of the most cited HPC numerical software projects.
- **Why it fits PA-AKG.** Trilinos has decades of numerical analysis, published benchmarks, and a large test corpus. AI-suggested changes to solver code carry real numerical-correctness risk — exactly the "silently invalidate simulation campaigns" failure mode called out in the 18E abstract. The KG can encode algorithm ↔ benchmark ↔ hardware-target relations and catch recommendations that violate them.
- **Evaluation handle.** Pick one package (e.g., Belos for iterative solvers, or Tpetra for distributed linear algebra) to keep the scope bounded. Use Trilinos's built-in unit/regression test corpus as ground truth for E1.
- **Risk.** Trilinos is large; scope discipline is essential.

### 3. **LAMMPS** *(Tertiary anchor — full application)*

- **What it is.** Large-scale Atomic/Molecular Massively Parallel Simulator. Classical molecular dynamics code, widely used in materials science and chemistry.
- **Sandia role.** Sandia-originated, maintained by a multi-lab community. GPL-licensed, public on GitHub.
- **Why it fits PA-AKG.** LAMMPS has an exceptionally public history of performance work: GPU ports (via Kokkos!), pair-style optimizations, benchmark publications. This gives the KG a rich ingestion target, and gives PA-AKG a story connecting the three anchors (LAMMPS → Trilinos-style solvers → Kokkos execution).
- **Evaluation handle.** A well-known pair-style (e.g., `lj/cut`, `eam`) and its Kokkos port provide a concrete AI-assisted translation task with auditable before/after benchmarks.
- **Risk.** LAMMPS is broad — narrow the evaluation to a specific pair-style or neighbor-list path.

---

## Why These Three Together

| Layer | Code | Translation challenge PA-AKG addresses |
|---|---|---|
| Execution portability | Kokkos | CPU ↔ GPU ↔ accelerator refactors with correct execution/memory spaces |
| Numerical framework | Trilinos | Solver changes preserving convergence + numerical stability |
| End-to-end application | LAMMPS | Pair-style port with auditable performance + numerical validation |

This three-code stack exercises all four PA-AKG evaluation axes:

- **E1 — Span-level evidence alignment:** test suites and published benchmarks give ground truth for recommendations.
- **E2 — Canonicalization consistency:** same algorithm (e.g., SpMV) appears in all three layers — does the KG canonicalize it consistently?
- **E3 — Traceability completeness:** AI recommendations must trace back to concrete benchmark or test evidence.
- **E4 — Longitudinal stability:** real git history across versions provides the longitudinal signal.

All three are Sandia-originated, which makes Steinmetz's validation role unambiguous on the cover sheet and in Criterion 3 (Team).

---

## Alternative / Backup Candidates

Kept on the bench in case the anchor set needs adjustment:

| Code | Domain | Why it could substitute |
|---|---|---|
| **SPARTA** | Direct Simulation Monte Carlo | Sandia-originated like LAMMPS; narrower scope |
| **Sierra / Albany** | Multiphysics finite element | Strong Sandia connection, but parts are export-controlled — friction for provenance publication |
| **EMPIRE** | Plasma / electromagnetics | Sandia code, but largely restricted — breaks the "public provenance" criterion |
| **AMReX** | Block-structured AMR | Not Sandia-led (LBNL/ECP), but in E4S; strong GPU port history |
| **OpenMC** | Monte Carlo neutron transport | Not Sandia, but small, open, well-benchmarked; easy evaluation target |
| **NWChem** | Computational chemistry | PNNL, not Sandia; would weaken the Sandia-role narrative |
| **PETSc** | Solver library (alternative to Trilinos) | ANL, not Sandia; duplicates Trilinos's role |

**Recommendation:** keep the Sandia-anchored set (Kokkos / Trilinos / LAMMPS) unless an industry partner brings a specific code preference, in which case AMReX or OpenMC are the cleanest public substitutes.

---

## Open Questions for the Team

1. **Steinmetz confirmation.** Which Kokkos / Trilinos / LAMMPS subsets does he have direct validation-corpus access to under existing data agreements?
2. **Industry partner overlap.** If HPE, NVIDIA, or AWS joins the team (per the reviewer feedback in `files/full-proposal-plan-18E.md:30`), do they have a preferred code that should bump one of the three?
3. **Scope cut.** Full proposal is 5 pages. Do we describe all three anchors, or lead with one (Kokkos) and treat the other two as "stretch" corpora?

---

*Source: derived from `files/full-proposal-plan-18E.md` (reviewer feedback + data-source TODOs) and the submitted 18E abstract (`abstract_18E/abstract.tex`).*
