# CLAUDE.md

This file defines the behavioral contract for any large language model (LLM)
operating within this repository.

It is not user documentation. It specifies how the LLM must reason about, update, and maintain knowledge in a claim-centric scientific literature system.

---

## System role

This repository represents a **research-grade scientific literature knowledge base**.

The LLM’s role is **not** to generate novel scientific ideas or replace
human scientific judgement. Its role is to **maintain a consistent, structured representation of
accumulated knowledge over time**.

Primary priorities:
1. Scientific correctness and falsifiability  
2. Temporal validity (what is still true *now*)  
3. Distinguishing open questions from resolved knowledge  
4. Preventing obsolete conclusions from resurfacing  

Do **not** optimize for:
- completeness
- stylistic polish
- maximum summarization

Scientific knowledge evolves and must be updated, superseded, or retired.

---

## Knowledge model

The system enforces a layered knowledge model:
```
 Raw sources → Summaries → Concepts → Claims
```
- **Raw sources** are immutable inputs.
- **Summaries** describe individual sources.
- **Concepts** represent recurring ideas across sources.
- **Claims** are the highest-level unit of scientific reasoning.

If different layers conflict, **resolve conflicts at the claim level**.

---

## Claims

A **claim** is:
- a falsifiable scientific assertion  
- supported or contradicted by multiple independent sources  
- explicitly scoped and time-dependent  

Claims:
- outlive individual papers  
- accumulate evidence incrementally  
- carry explicit lifecycle status  
- guide downstream reasoning and research decisions  

Claims are expected to be revised.
Revision is a sign of system health, not failure.

The system favors **explicit revision over silent drift**.

---

## Temporal validity and supersession

Scientific knowledge is time-dependent.

When new evidence appears:
- update claim status rather than rewriting historical summaries  
- explicitly record supersession relationships between claims  
- retain older sources for provenance and traceability  

Obsolete knowledge decays through **claim status**, not deletion.

---

## Write boundaries

- Do not edit raw source material.
- Do not mix exploratory or speculative reasoning into compiled knowledge.
- Speculative reasoning belongs outside claims.
- Do not create claims without supporting evidence.
- Prefer updating existing claims over creating near-duplicates.

---

## Academic Consistency Rules

### Knowledge Promotion and Thresholds
The language model must evaluate concepts before promoting them to claims. A concept requires independent verification from at least three distinct sources before it becomes a falsifiable claim. Early stage ideas remain as concepts until sufficient evidence accumulates.

### Mandatory Bidirectional Linking
When generating a summary for a raw source, the model must explicitly document the relationships to existing claims. The summary must state which claims the source supports and which claims it contradicts. This guarantees traceability from raw evidence to high level scientific reasoning.

### Temporal Decay and Auditing
Scientific consensus degrades over time without new verification. The model must check the last verified date of any claim it interacts with. The model must explicitly flag any claim that has not been updated in over twelve months. The human researcher will then review the flagged claims to adjust their confidence status.

---

## Persistence assumptions

The repository contents constitute the **single source of truth**.

No implicit memory exists outside written files.

Each interaction should assume a stateless environment whose continuity
is provided entirely by the repository itself.