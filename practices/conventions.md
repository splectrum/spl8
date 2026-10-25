# Conventions — kept, changed, new — draft

Status: **draft proposal**

Sorted from spl7's `CLAUDE.md` and `.claude/rules/conventions.md`.

## Kept

- **Philosophy first.** The seed principles ground design decisions.
- **Maximum beneficial autonomy.** If the system can do it, it should.
- **Technology decisions are AI's domain.** Decide.
- **Build, don't plan endlessly.** If wrong, fix it.
- **KISS / aggressive simplification.** If the substrate provides it, don't
  reimplement it; defer what is optional.
- **Engineering as conversation.** Natural language at the interaction level,
  rigid implementation beneath. The boundary that disappears is the one
  between natural and structured language.
- **Ask in prose.** No option-picker questions.
- **Task list in the repo** (`plan/tasks.md`) — durable, out of the always-on
  context.
- **Scrubbed logs; parameterised cluster config.** `.env` gitignored,
  `.env.example` committed; logs pass through `scrub.sh` before commit.
- **Probes.** Re-runnable de-risking setups with a committed run log.
- **Reference docs for AI readers**, kept fresh by a recurring agent; every
  page carries a Sources block.
- **Doc prompts carry content, not site mechanics.**
- **Settled vision, calibrated.** Distillation, not demolition.
- **Pressure-point approach** — invest properly when pressure arrives.

## Changed

| spl7 | Engineering repo |
|---|---|
| Agree the approach before any agent, background process or cross-repo action | Act freely inside implementation space; propose and stop at the logical layer and outward-facing actions (`autonomy.md`) |
| Proof is a committed run log / a browser UI | Proof is a green gate; logs are attached evidence (`gate.md`) |
| One folder per phase, scripts duplicated, journey in the tree | Journey lives in git history and run artefacts; the tree holds the current product. `probes/` stays |
| Coordination repo + local workspace repos + absolute `~/` paths | One GitHub repository reachable by cloud sessions; relative paths only |
| Commit when the user asks or a coherent piece is ready | Commit when the gate is green and the piece is coherent |
| Memory flow: session bank → repo rules | Unchanged in spirit; the repo stays the durable home |

## New

- **Definition of done = gate exit code 0.**
- **Boundary enforced by repository mechanics** (code owners, branch
  protection), not only by agreement.
- **Specs are examples.** Natural-language intent is turned into examples and
  conformance cases the human can read.
- **Token and run budgets.** Unattended agents get explicit budgets; the
  evolutionary process needs a fitness signal, not just activity.

## Open

- Whether `plan/tasks.md` becomes the queue unattended agents pull from, or
  GitHub issues take that role.
- Whether agent teams are used, and under what budget.
