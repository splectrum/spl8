# spl8

Design repository for the next phase of SPLectrum engineering.

spl8 is **logical space**. Here we discuss and agree two things:

1. **Working practices** for highly autonomous human-AI engineering —
   who decides what, how work is verified, how it flows.
2. **The design** the engineering repo will build first — distilled from
   spl6, spl7 and splectrum.world, not rediscovered from scratch.

When both have settled, a separate **engineering repository** is created for
execution. That repo is implementation space: it runs autonomously from day
one against the practices and design agreed here.

## Layout

| Path | What lives there |
|---|---|
| `CLAUDE.md` | How we work *in this repo* |
| `practices/` | The working practices being agreed for the engineering repo |
| `design/` | The distillation — settled, superseded, open — and new design |
| `probes/` | Small grounding experiments, each with a committed run log |
| `roadmap.md` | The roadmap, planned logarithmically |
| `open-questions.md` | Everything still to decide, in one place |

## Exit condition

spl8 is done when these exist and have been ratified:

- [ ] Working practices — as the draft `CLAUDE.md` for the engineering repo
- [ ] The autonomy boundary — what the AI does freely, what waits for the human
- [ ] The gate — the definition of done, as one command and one exit code
- [ ] The base-layer design — URI + XPath, mutable/immutable, change-stream duality
- [ ] The first slice to build

Anything still moving is marked **open**, not pinned.

## After spl8

To be decided (see `open-questions.md`): whether spl8's settled content
graduates into the engineering repo as its `logical/` layer and spl8 is
archived, or spl8 continues as the permanent logical repo alongside it.

## Status of content

Everything here starts as **draft proposal**. A document is settled only when
its status line says so.
