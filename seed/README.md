# SPLectrum roadmap

Status: **seed** — prepared in spl8, 2026-10-25

The roadmap repo plans SPLectrum engineering over a longer cycle and spawns a
**dev env repo** for each phase. It is also the home of the settled design and
working practices that every phase draws on.

This is pre-P2P: plain GitHub repositories and Claude cloud sessions.

## State model

- **The tree holds current state only:** the current roadmap, the settled
  design and practices, queued phases, open questions.
- **Commits hold the transitions:** executed phases (request and response),
  revisions of the plan with their reasons, and discussions in distilled form.
- **Transient data is committed, then dropped from state.** Discussions and
  executed items live in history, not in the tree.

## Phases

A phase runs in its own dev env repo, executed by one Claude cloud session.

1. **Queued** — a phase request in `queue/`.
2. **Spawned** — a dev env repo is created and attached to a new session.
   For now the human creates the repo.
3. **Executed** — the session works through the phase, following
   `practices/dev-env.md`.
4. **Extracted** — components go to their single-concern repos; practices
   that settled go into `practices/`; design learnings go into `design/`.
5. **Recorded** — a commit here removes the phase request. Its message holds
   the phase summary, a link to the dev env repo's final commit, and the
   component versions it produced.
6. **Archived** — the dev env repo is archived, read-only: the record of how
   the phase was done.

## Layout

| Path | What lives there |
|---|---|
| `CLAUDE.md` | How to work in this repo |
| `roadmap.md` | The plan, logarithmic: detailed near, sketched further out |
| `queue/` | Queued phase requests |
| `design/` | Settled design, and design still open |
| `practices/` | Working practices, including the dev env repo practice |
| `open-questions.md` | What is still to decide |
