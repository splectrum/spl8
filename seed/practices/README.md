# Working practices

| Document | Covers |
|---|---|
| `dev-env.md` | How a cloud session works over a dev env repo — one phase |
| `requirements.md` | Requirements as executions narrated in natural language |
| `autonomy.md` | The boundary: who decides what, and earning autonomy |
| `gate.md` | The definition of done |
| `conventions.md` | Conventions kept, changed and new since spl7 |

## The shift from spl7

spl7 was built for a collaborative rhythm: the human in the loop on most
actions, and proof as evidence for a human to read. Its stated target already
pointed further — physical fully AI-autonomous, logical interactive and
collaborative — but its working rules held autonomy back: per-action
agreement, run logs instead of a gate, and work spread over local repos out of
reach of a cloud session.

The new practice keeps the target and changes the mechanics: a boundary
instead of per-action agreement, an executable gate, and short-lived dev env
repos reachable by cloud sessions, planned from one roadmap repo.
