# Autonomy boundary — draft

Status: **draft proposal**

## Principle

Autonomy comes from verification, not from permission. The AI can act
unattended exactly as far as it can check its own work. So the boundary is
drawn where checking stops being mechanical and starts being a matter of
meaning.

## The line: meaning

The engineering commitment *logical over physical* names physical
implementation as the natural place for maximal AI autonomy. Models now also do
credible design work, so the line is drawn at **meaning** rather than strictly
at logical vs physical:

| Human | Meeting point | AI |
|---|---|---|
| Philosophy, commitments, vocabulary | Examples and conformance cases | Code, tests, tooling |
| Scope and direction | Proposed design options and decision records | Environments, containers, CI |
| What a thing *means* | The AI states its reading; the human confirms | Refactoring, dependencies, structure |
| Ratifying design | | Drafting design for ratification |

## How it works in the engineering repo

- **Act freely** inside implementation directories (code, test, stack/
  infrastructure). Merge on a green gate.
- **Propose and stop** at the logical layer, the spec/examples layer, and
  anything outward-facing (publishing, the public site, other repos).
- **Natural language in, checkable examples out.** The human states intent in
  prose. Before building on it unattended, the AI turns it into examples or
  test cases and the human glances at them — the AI states which meaning
  context it took the words in.
- **Enforced, not just agreed.** The boundary is made real by repository
  mechanics (code owners and branch protection on the logical directories),
  so it holds when nobody is watching.

## Earning autonomy

Collaboration is earned. Autonomy widens in steps as the gate proves itself:

1. AI proposes changes; the human merges.
2. Auto-merge for test-only and refactoring changes on a green gate.
3. Auto-merge for whole components once the gate has caught enough of the
   AI's own mistakes to be trusted.

## Open

- Exactly which directories sit on each side of the line.
- Whether public documentation prompts also wait for human review.
- How the human is notified of work done unattended (summary cadence).
