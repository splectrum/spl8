# Components and agents

Status: **agreed in discussion** (2026-10-25)

Builds on `natural-language.md`.

## Software components

A software component has a **structured core**, bound to a versioned schema,
with translation at its edges:

- **On invocation**, a natural-language request is mapped to the component's
  input schema. If it does not map, the component does not run, and the reply
  says why.
- **On completion**, the structured result is rendered as natural language,
  with the exact data embedded as blocks. Every result is itself a valid
  natural-language document.

Components declare a schema and contain no translation code. Translation is
one shared capability, driven by each component's schema.

Components call each other directly in structured form. Translation happens
only where a person or an agent is at the boundary.

## Agents

Agents are components whose native interface is natural language. They
interpret, coordinate, diagnose and narrate, and they use software components
through their structured interfaces.

**Rule: agents only write natural-language data, unless they use a software
component to write it.**

- Structured data is therefore valid by construction: every structured datum
  has a component in its provenance, with a schema version.
- Agent writes are still git commits, so they are attributed, versioned and
  audited.
- A structured block embedded in an agent's natural-language document is part
  of the text. It becomes structured data only when a component projects it.
- The gate can enforce the rule from commit provenance.

Messages between agents are natural-language documents in the repository:
stored, audited and replayable. The next agent wakes on them.

## Audit

Each invocation records the request, the structured form it was mapped to, and
the result. The reading of every request is part of the record.

## Without a model

Translation and agents need a model; the structured core does not. If no model
is reachable, the agent paths stop, and the components and their structured
interfaces keep working.

## Open

- How translation is provided and versioned (see also `natural-language.md`).
