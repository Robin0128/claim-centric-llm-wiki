# Claim‑Centric LLM Wiki
**A claim‑centric, temporally‑aware workflow for scientific research**

---

## Overview

This repository provides a **research‑grade workflow template** for managing scientific literature with the assistance of large language models (LLMs).

It is designed for researchers who:

- work with **large and evolving bodies of literature**
- need to clearly distinguish **open questions from resolved knowledge**
- want accumulated understanding rather than repeated rediscovery
- use LLMs as *research assistants*, not note‑taking tools

The central idea is simple:

> **LLMs should compile knowledge.  
> Researchers should make scientific judgements.**

This repository encodes that division of labor explicitly.

---

## Conceptual background and attribution

The high‑level philosophy of this workflow is inspired by prior discussions of
LLM‑maintained knowledge bases, most notably the *LLM Wiki* idea articulated
by **[Andrej Karpathy](https://x.com/karpathy/status/2039805659525644595)**.

In addition, the **four‑layer structural separation**
(raw inputs → compiled knowledge → exploratory reasoning → final artifacts)
is informed by practical implementations in the community, particularly
the open‑source project
**[gatelynch/llm‑knowledge‑base](https://github.com/gatelynch/llm-knowledge-base)**.

This repository does not fork or re‑implement any existing codebase.
Instead, it adapts and extends these ideas toward a **claim‑centric,
temporally‑aware research workflow**, with stronger emphasis on:

- claims as the primary unit of scientific reasoning
- explicit temporal validity and supersession
- long‑term stability under continuous literature growth

All remaining design decisions and abstractions are independently developed
and motivated by practical use in active scientific research.

Any errors or limitations are entirely my own.

---

## What this repository is—and is not

### This repository **is**
- a workflow template for scientific literature management
- a reference structure for LLM‑assisted knowledge compilation
- designed for long‑term research use (months to years)

### This repository **is not**
- a note‑taking system
- a personal Zettelkasten or “second brain”
- a RAG database over PDFs
- a collection of example research content

It contains **structure, rules, and templates**, not your actual literature corpus.

---

## Core principles

### 1. Papers are evidence, not knowledge

Individual papers are sources of evidence.  
Knowledge exists only after **cross‑paper synthesis and judgement**.
The workflow enforces a unidirectional pipeline
(from the perspective of research decision‑making):

```
 raw papers → summaries → claims
```

Intermediate representations (such as extracted concepts)
exist internally to support reasoning, but claims are the
primary unit exposed for research decisions.


---

### 2. Claims are the primary unit of reasoning

The central abstraction is a **claim**:

> A falsifiable scientific assertion supported or contradicted by multiple papers and evolving over time.

Claims:
- outlive individual papers  
- absorb new evidence incrementally  
- prevent obsolete conclusions from resurfacing  
- guide future research decisions  

The hierarchy is explicit:
```text
 Claims  >  Concepts  >  Summaries
```

If a summary conflicts with a claim, **the claim governs interpretation**.

---

### 3. Temporal validity is first‑class

Scientific knowledge changes.

Each claim carries an explicit lifecycle status:
- `Open`
- `Partially Resolved`
- `Resolved`
- `Context‑dependent`
- `Obsolete`

Old papers are never deleted.  
Their influence decays **only through claim status**, not removal.

---

### 4. Clear responsibility split: LLM vs human

**LLMs are responsible for**
- summarizing sources
- extracting recurring concepts
- integrating evidence into claims
- maintaining indices and health checks

**Humans are responsible for**
- deciding what matters
- judging when questions are resolved
- defining scope and assumptions

This separation keeps responsibility explicit and auditable.

---

## Repository structure

```
raw/            # Immutable inputs (papers, articles, notes)
wiki/           # LLM-maintained compiled knowledge
  ├── summaries/  # One summary per source
  ├── concepts/   # Cross-source recurring ideas
  ├── claims/     # Scientific claims (highest level)
  └── indexes/    # Navigation and dashboards
brainstorming/  # Exploratory Q&A and reasoning logs
artifacts/      # Research outputs (papers, projects)
```
Each layer has a single responsibility and is intentionally separated.

---

## The role of `CLAUDE.md`

`CLAUDE.md` functions as a **behavioral contract** for the LLM.

It specifies:
- system role and priorities
- what constitutes a claim
- how temporal validity and supersession are handled
- assumptions about persistence and responsibility boundaries

Each session begins from these constraints; nothing is implicit.

---

## Claim template

All claims must conform to the schema defined in: wiki/claims/CCLAIM_TEMPLATE.md

The template enforces falsifiability, scope boundaries, structured evidence tracking, and lifecycle‑aware updates.

---

## Recommended workflow

### Adding new literature

1. Place papers into `raw/papers/`
2. Run the LLM compilation step
3. Let the LLM generate summaries and update existing claims
4. Review **only claim‑level changes**

Most papers should **not** generate new claims.

---

### When to create a new claim
A new claim should be created only under strict conditions. The conclusion must change whether a question is open or resolved. It may also abstract multiple papers into a stable mechanism. Furthermore, creating a claim is justified if it corrects a widespread incorrect assumption or affects future research investment decisions.

---

## Why this approach scales

Conventional workflows fail at scale because:
- RAG rediscoveres the same conclusions repeatedly
- note systems flatten temporal validity
- summaries accumulate without convergence

This workflow forces convergence.

Over time:
- resolved claims accumulate
- active research space contracts
- cognitive load decreases
- research decisions become faster and more confident

---

## Intended audience

This template is intended for:
- postdoctoral researchers
- PhD students managing large literatures
- principal investigators seeking long‑term research memory
- interdisciplinary researchers spanning multiple domains

---

## Getting started

1. Clone this repository
2. Read `CLAUDE.md`
3. Add your first paper to `raw/`
4. Compile and iterate

---

## Tool‑specific implementations (optional)

This repository is intentionally **tool‑neutral**.

If you are using an LLM environment with built‑in commands
(e.g. Claude Code, Codex, or other agent runtimes),
see:

- `implementation-mapping.md`

for a mapping between the conceptual workflow defined here
and common tool‑specific implementations.

---
## Prompt usage patterns (optional)

This repository intentionally separates **knowledge structure**
from **interaction patterns**.

For guidance on how to interact with an LLM when performing common tasks
such as compilation, auditing, or exploratory thinking,
see:

- `Prompt Guide.md`

This guide provides task‑specific prompting patterns while respecting
the invariants defined in `CLAUDE.md`.

---

## Acknowledgements

The conceptual foundation of this project is inspired by
**Andrej Karpathy’s LLM Wiki idea**
as introduced in his
[original LLM Wiki post](https://x.com/karpathy/status/2039805659525644595)
and the accompanying
[idea file](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f).

The four‑layer structural separation used in this repository
(raw inputs → compiled knowledge → exploratory reasoning → final artifacts)
is informed by practical community implementations, in particular
the open‑source project
**[gatelynch/llm‑knowledge‑base](https://github.com/gatelynch/llm-knowledge-base)**.

This repository does not reuse or fork any existing codebase.
Instead, it adapts and extends these ideas toward a
**claim‑centric, temporally‑aware workflow**
tailored for long‑term scientific research.

All interpretations, extensions, and remaining limitations are my own.

---

## Philosophy

> **Knowledge should accumulate.  
> Time should reduce uncertainty, not increase it.**

---
