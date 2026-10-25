# Roadmap

Status: **draft proposal** (2026-10-25)

Planned logarithmically: detailed for what comes now, less detailed further
out. Each stage is entered when the previous one has proved itself, not by date.

Two lines run through the whole roadmap:

- **The product:** Mycelium, built up block by block from git objects.
- **The way of working:** the autonomy ladder. Each rung is earned by evidence:
  bundles that needed no correction, and a gate that caught the agents' own
  mistakes.

## Now: close spl8, open the engineering repo

**1. Settle what the first engineering step needs.**
- Revise the gate for the git-first start: tests are lists of normal commands;
  the verdict is an exit code.
- Agree the task-record form: one folder per task, holding the request and,
  when done, the response; a status line with a few fixed words.
- Agree the minimum event format: one structured line per event, with node,
  operation, correlation id and cause.
- Decide the engineering repo's name, and whether spl8 graduates into it or
  continues beside it.
- Reconcile natural language as the authority for meaning with the settled
  authority split.

**2. Create the engineering repo.**
A self-contained repo, no other tools:
- `CLAUDE.md` built from the agreed practices;
- the task queue;
- the gate command;
- instrumentation from the first line of code;
- a first deterministic narrative tool turning the event log into prose.

**3. First slice, first bundle.**
- In-memory, transient git objects: blob, tree, commit, ref.
- Normal commands to create, read and commit them.
- Every operation instrumented.
- Given as the first requirement in the new form, an execution talked through
  in natural language, and run through the whole loop to produce the first
  bundle. Autonomy rung 1: implementation automated, interpretation confirmed
  and bundle reviewed by the human.

## Next

- URI and XPath over git trees, with pointer records and always-array results.
- Mutable working state over the immutable objects; the commit log read as a
  change stream.
- Translation v0: natural-language requests mapped to a component's schema, and
  results rendered back.
- Instrumentation config, with profiles per deployment type.
- The node core as a host-neutral Bare module, with filesystem persistence.
  Early mobile inclusion starts here: nothing in the core that a phone lacks.
- Autonomy rung 2 when the record supports it: build and merge on a green gate
  within an agreed requirement.

## Later

- Hyperdrive persistence and replication on the swarm.
- The deploy → run → teardown swarm stack.
- Test runners outside the cloud: a home runner (including a phone on WiFi)
  and an internet runner, picking up queued test requests and writing results
  back to the repo.
- The phone as reader, then as owner, with an always-on companion peer.
- AVRO: XPath drills into data structures. The document paradigm.
- Agents as components of the running software.
- The working repo becomes a Mycelium repo.
- Autonomy rung 3: design proposals drafted by the AI, ratified by the human.

## Horizon

Multi-paradigm Mycelium (relational, key-value, graph) · Hypercore streams ·
one owner on several devices · real networks and relays · iOS · circles ·
interop at the edges · autonomy rung 4: from requirement to bundle.

## Always discussed, at every stage

Anything touching meaning, the philosophy or a settled commitment; changes to
the working practices; anything irreversible or outward-facing.
