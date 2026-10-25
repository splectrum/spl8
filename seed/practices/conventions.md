# Conventions — kept, changed, new

Sorted from spl7's `CLAUDE.md` and `.claude/rules/conventions.md`.

## Kept

- **Philosophy first.** The seed principles ground design decisions.
- **Maximum beneficial autonomy.** If the system can do it, it should.
- **Technology decisions are AI's domain.** Decide.
- **Build, don't plan endlessly.** If wrong, fix it.
- **KISS and aggressive simplification.** If the substrate provides it, don't
  reimplement it; defer what is optional.
- **Engineering as conversation.** Natural language at the interaction level,
  rigid implementation beneath.
- **Ask in prose.** No option-picker questions.
- **Scrubbed logs; parameterised config.** `.env` gitignored, `.env.example`
  committed; logs scrubbed before commit.
- **Probes** for de-risking, with a committed run log.
- **Reference docs for AI readers**, kept fresh by a recurring agent; every
  page carries a Sources block.
- **Doc prompts carry content, not site mechanics.**
- **Settled vision, calibrated. Distillation, not demolition.**
- **Pressure-point approach.** Invest properly when pressure arrives.
- **The journey is kept; the installable graduates clean.**

## Changed

| spl7 | Now |
|---|---|
| Agree the approach before any agent, background process or cross-repo action | Act freely inside implementation space; propose and stop at the logical layer and outward-facing actions |
| Proof is a committed run log or a browser UI | Proof is the gate's exit code; logs and narratives are evidence |
| One folder per phase, scripts duplicated | One dev env repo per phase; the archived repo is the journey |
| Coordination repo, local workspace repos, absolute `~/` paths | A roadmap repo plus dev env repos reachable by cloud sessions; relative paths only |
| Task list in `plan/tasks.md` | Queued requests as files; executed requests in commit messages |
| Commit when a coherent piece is ready | Commit at checkpoints, batched, never per edit |

## New

- **Natural language is primary**, with structured blocks embedded verbatim
  (`design/natural-language.md`).
- **Agents only write natural-language data**, unless they use a software
  component (`design/components-and-agents.md`).
- **Requirements are narrated executions** (`requirements.md`).
- **Logarithmic planning.**
- **Token and run budgets** for unattended agents.
