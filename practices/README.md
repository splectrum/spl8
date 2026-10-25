# Working practices — draft

Status: **draft proposal**

The working practices for the engineering repo. When settled, this folder
becomes that repo's `CLAUDE.md` and rules.

| Document | Covers |
|---|---|
| `autonomy.md` | The boundary: who decides what, where the human meets the AI |
| `gate.md` | The definition of done — how work verifies itself |
| `conventions.md` | What carries over from spl6/spl7, what changes, what is new |
| `requirements.md` | Requirements as natural-language executions |

## The shift from spl7

spl7 was built for a collaborative rhythm: the human in the loop on most
actions, evidence (run logs, a browser UI) read by a human. Its stated target
already pointed elsewhere — *physical fully AI autonomous; logical interactive
collaborative* — but the working rules held autonomy back:

- "Agree the approach before acting" required confirmation before any agent,
  background process or cross-repo action — a per-action brake.
- Proof was **evidence for a human** (session logs, a node-switcher UI), not a
  **gate** an agent can act on.
- Work spread over several repos, some only on a local machine, with absolute
  paths — out of reach of a cloud session.

The new pattern keeps the target and changes the mechanics: a clear boundary
instead of per-action agreement, an executable gate instead of read-only
evidence, one reachable repo instead of a local constellation.
