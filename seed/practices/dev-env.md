# The dev env repo

Status: **agreed in discussion** (2026-10-25); to be refined by the first phases

## One session, one repo, one phase

A dev env repo is created for one phase and worked by one Claude cloud
session. When the phase is done, its results are extracted and the repo is
archived. Each session starts with fresh context from the roadmap repo rather
than an accumulated history. Every commit carries a `Claude-Session` trailer,
so the archive and the session transcript link to each other.

## Layout

| Path | What lives there |
|---|---|
| `README.md` | The phase: its goal and its exit condition |
| `CLAUDE.md` | How to work in this repo |
| `queue/` | Requests waiting to be executed |
| `<component>/` | One folder per component |
| `.gittrees` | Which component folder syncs to which single-concern repo |

**Each component folder stands on its own:** its own README, package
definition and tests. A component uses another only through its package name,
never through a relative path into a neighbour's folder, so a split-out repo
builds on its own. The gate builds and tests each folder in isolation.

## Requests

A request that waits is a file in `queue/` with a sortable name, for example
`0007-blob-objects.md`. It is natural language with a few fixed lines at the
top:

- **Status:** `queued` or `blocked`
- **From:** `interactive` or `planned`
- **Parent:** the parent request's id, for planned steps

Only waiting requests are in `queue/`. Executed requests leave the tree.

- **Interactive.** A request executed straight away never gets a queue file;
  it goes directly into the commit that executes it.
- **Planned.** When a task is broken down, the task is the parent request and
  its steps are queued as children, each narrated in natural language.
  Queuing a breakdown is one commit, and that commit is where the human sees
  the plan and can redirect it before anything runs.

## Execution and commit

At a checkpoint, one or more queued steps are executed and the gate is run.
Then one commit holds:

- the changes to code and docs;
- the executed queue files, removed;
- a message recording, for each request, the request text and the response:
  what was done, the verdict, and where the evidence is.

Fixed trailers in the message — `Request-Id`, `Parent`, `Verdict` — make any
request's history findable with `git log --grep`. The commit that completes a
parent carries the task's summary narrative; that message is the bundle.

Discussions are recorded the same way: distilled into the checkpoint commit's
message, not kept in the tree.

**Failed** steps are committed with the failure as the response; the request
stays queued with its status updated. **Blocked** requests carry their question
in the request file, with status `blocked`, until the human answers.

Bulky evidence such as run logs goes on an append-only `evidence` branch,
referenced from the message, so `main` stays lean.

## Commit discipline

- Few commits, at checkpoints. Never one per edit.
- Edits are made only when checkpointing: a cloud session cannot end a turn
  with uncommitted changes, so editing during discussion forces commits.
- Batch several steps into one checkpoint where they belong together.

Too many automated commits risks the GitHub account being suspended.

## Cloud constraints

The session's clone is shallow; it can push branches but not tags or other
refs, cannot delete branches, cannot use GitHub's GraphQL API, and cannot
create repositories. Operations that need more — full-history subtree splits,
repo creation, pushes to many repos — run locally.

## Closing a phase

The final commit carries the phase narrative. Components are split out to
their single-concern repos, and the phase is recorded in the roadmap repo. The
repo is then archived.

## Watchers (next)

Local processes that pick up work the cloud session cannot do:

- **Subtree sync.** One-way from the dev env repo to the single-concern repos,
  on an interval, pushing only when a split has changed; built on spl6's Bare
  `lib/git` (`.gittrees`, subtree push and pull). Deploy keys per repo rather
  than personal credentials.
- **Local test runner.** Runs queued tests the cloud cannot — a phone on WiFi,
  real networks — and commits results, batched.

## Open

- Whether a generated overview of pending and done work is needed, or the
  `queue/` folder and the log are enough to read on a phone.
- Whether to bring in code from earlier workspaces, or start fresh and port
  what is needed.
