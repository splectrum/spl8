# Roadmap

Status: **draft** — seeded from spl8, 2026-10-25

Planned logarithmically: detailed for now, less detailed further out. A stage
is entered when the previous one has proved itself, not by date.

Two lines run through it:

- **The product:** Mycelium, built up block by block from git objects
  (`design/base-layer.md`).
- **The way of working:** the autonomy ladder (`practices/autonomy.md`). Each
  rung is earned by evidence — bundles that needed no correction, and a gate
  that caught the agents' own mistakes.

We start with an interactive AI agent in a cloud session, extended with local
processes triggered by watchers, and build the node execution environments bit
by bit. Each piece of today's tooling replaced by a node component is a
milestone.

## Now: first phases

Independent code blocks, with no dependencies between them. Each phase is its
own dev env repo and session, done in any order.

**Mycelium objects.** In-memory, transient git objects — blob, tree, commit,
ref — content-addressed, with normal commands to create, read and commit them.
Every operation emits one structured event line. Tests are lists of normal
commands; the verdict is the exit code. The first requirements are given as
executions narrated in natural language.

**P2P node.** The spl6 primitives re-established on current Bare: peers
discover and connect on a private testnet. Without the deprecated `pear run`;
the node core is a plain Bare module.

**Docker node stack.** Deploy → run → teardown with a minimal node, first
running the Mycelium commands in a container. Includes the probe: does a
compose swarm with peer discovery run inside a cloud session?

All three follow the dev env practice. The first phases also shape the
practice itself, and a dev env template is extracted once it has settled.

## Next

- URI and XPath over git trees: pointer records, always-array results.
- Mutable working state over the objects; the commit log read as a change
  stream.
- Translation v0: natural language mapped to a component's schema and back.
- Instrumentation config with profiles; a deterministic narrative from the
  event log.
- Local watchers: one-way subtree sync to single-concern repos; a local test
  runner.
- The dev env template.

## Later

- Persistence behind the objects: filesystem, then Hyperdrive.
- Replication on the swarm; the node's own git transaction model, mounts and
  multi-writer (`design/node-git.md`).
- Test runners outside the cloud: home (including a phone on WiFi) and
  internet.
- Mobile: the phone as reader, then owner, with an always-on companion.
- AVRO: XPath into data structures; the document paradigm.
- Agents as components of the running software.
- The working practice moves onto node components.

## Horizon

Multi-paradigm Mycelium (relational, key-value, graph) · Hypercore streams ·
one owner on several devices · real networks and relays · iOS · circles ·
interop at the edges · repos become Mycelium repos · autonomy rung 4: from
requirement to bundle.

## Always discussed

Anything touching meaning, the philosophy or a settled commitment; changes to
the working practices; anything irreversible or outward-facing.
