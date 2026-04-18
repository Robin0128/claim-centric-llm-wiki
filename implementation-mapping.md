# Implementation Mapping (Tool‑Neutral)

This document maps the **conceptual workflow primitives**
defined in this repository to possible implementations
in specific LLM tools or agent runtimes.

This repository intentionally does **not** ship tool‑specific commands.
Instead, it specifies **behavioral invariants and knowledge constraints**.

Implementations are expected to respect these mappings
without assuming any particular user interface or command system.

---

## Design intent

The core goal of this repository is to define:

- what knowledge states must exist
- how those states evolve over time
- where judgement boundaries are enforced

It does **not** prescribe:
- how steps are triggered
- what UI or commands are used
- which vendor tools are involved

This separation ensures longevity, portability,
and compatibility with future agent architectures.

---

## Conceptual workflow primitives

The high‑level workflow can be expressed in terms of
the following **conceptual primitives**:

| Primitive | Responsibility |
|---------|----------------|
| Ingest | Add new source material to `raw/` |
| Summarize | Produce source‑scoped summaries in `wiki/summaries/` |
| Concept extraction | Identify recurring concepts across multiple summaries |
| Claim update | Create, update, or supersede claims based on evidence |
| Index update | Refresh navigational or bookkeeping indexes |

These primitives describe **what must happen**,
not **how it is invoked**.

---

## Example mappings

### Claude Code (slash‑command based)

If you are using **Claude Code** or similar environments
with a slash‑command interface, the following mapping
is commonly observed:

| Claude Code command | Corresponding primitives |
|---------------------|--------------------------|
| `/compile` | Ingest → Summarize → Concept extraction → Index update |
| `/thinking-partner` | Exploratory reasoning (outside claims) |
| `/write-partner` | Pre‑writing exploration (outside claims) |
| `/health-check` | Consistency and structural audit |

Notes:
- Command availability and behavior depend on the local runtime.
- These commands are **not part of this repository**.
- Claim creation or updates still require judgement
  as defined in `CLAUDE.md`.

---

### Codex or other general LLM agents

For agents without built‑in commands or UI affordances,
equivalent behavior can be achieved by the following pattern:

- Read newly added files under `raw/`
- Generate one summary per source under `wiki/summaries/`
- Update or create concepts only when multiple summaries converge
- Update existing claims when evidence accumulates
- Create new claims only for stable, falsifiable assertions
- Keep exploratory reasoning outside `wiki/claims/`

The sequencing and automation level are implementation‑specific.
However, the knowledge invariants defined in:

- `README.md`
- `CLAUDE.md`

must always be respected.

---

## Non‑goals

This document intentionally avoids:

- prescribing concrete commands
- defining agent‑specific APIs
- encoding UI‑level procedures
- coupling the workflow to any single tool or vendor

Implementations may change. The knowledge model and reasoning constraints must not.

## Summary

- Commands are optional.
- Interfaces are temporary.
- Automation is replaceable.

### Claims and their lifecycle are the stable API.
This document serves as a bridge between tool‑neutral research methodology and concrete implementations without collapsing one into the other.