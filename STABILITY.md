# Stability Boundary Declaration (v1.0)

This document defines the **stability boundary** of the **Claim‑Centric LLM Wiki** as of version **v1.0**.

Its purpose is to clarify which aspects of the repository are **conceptually stable and intentional**, and which aspects are **explicitly allowed to evolve**.

This boundary exists to support **long‑term research use** without freezing the project prematurely.

---

## What v1.0 commits to (Stable)

The following elements are considered **stable at the conceptual level**. Future versions are expected to preserve these boundaries unless a **major version change** explicitly states otherwise.

---

### 1. Claims as the primary epistemic unit

- Claims are the highest‑level unit of reasoning in this repository.
- Claims must be:
  - falsifiable
  - evidence‑grounded
  - temporally scoped
- Summaries, concepts, and exploratory reasoning exist
  **only to support claims**.

This claim‑centric hierarchy is **non‑negotiable**.

---

### 2. Explicit temporal validity and supersession

- Scientific knowledge is treated as time‑dependent.
- Claims must carry:
  - lifecycle status
  - revision history
  - explicit supersession relationships
- Obsolescence is represented through **status updates**, not deletion.

Temporal validity is a **first‑class design concern**, not an annotation.

---

### 3. Separation of epistemic responsibility (LLM vs human)

- LLMs are responsible for:
  - summarization
  - evidence aggregation
  - consistency and structural checks
- Humans remain responsible for:
  - judgment
  - scope definition
  - claim acceptance, revision, and confidence

No v1.x version will eliminate or blur this responsibility boundary.

---

### 4. Tool‑neutral methodology

- The workflow does not depend on:
  - specific LLM vendors
  - command systems
  - user interfaces
- Tool‑specific implementations may be mapped,
  but **correctness is defined by methodology, not tooling**.

The method survives tooling changes.

---

## What v1.0 explicitly allows to evolve

The following areas are **intentionally not frozen** and may evolve without a major version change.

---

### 1. Prompting patterns and usage guidance

- Prompt structures in `Prompt Guide.md`
- Interaction heuristics
- Operational framing

These may change as LLM capabilities and interfaces evolve.

---

### 2. Documentation and pedagogy

- README wording
- Explanatory examples
- Clarifying diagrams or text

Improvements in clarity do not impact conceptual stability.

---

### 3. Implementation mappings

- Mappings to Claude Code, Codex, or other agent runtimes
- Automation strategies
- Batch or CI‑style workflows

These mappings are **illustrative rather than normative**.

---

## Explicit non‑goals (v1.0 and beyond)

This repository does **not** aim to become:

- a literature database
- a RAG system
- a note‑taking tool
- an autonomous research agent
- a source of scientific authority

It is a **workflow and reasoning scaffold**, not a knowledge oracle.

---

## Versioning philosophy

- **v1.0** establishes *conceptual stability*.
- Future **minor versions (v1.x)** may refine:
  - clarity
  - ergonomics
  - supporting tooling
- Only a **major version change (v2.0)** may revisit:
  - the claim‑centric model
  - epistemic responsibility boundaries
  - temporal validity assumptions

---

## Summary

> **v1.0 does not promise completeness.  
> It promises principled constraints.**

By defining what must not change, this repository makes clear where evolution is safe, and where it is not.
