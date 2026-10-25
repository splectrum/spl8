# Mycelium — the stack

Status: **agreed direction in discussion** (2026-10-25). Planned
logarithmically: detailed for the next step, less detailed further out.

## Endgame

A multi-paradigm repository (document, relational, key-value, graph, and
others), each paradigm with its own API, on one base: **git objects**, with
**URI and XPath** as the base paradigm.

## How it grows

By stacking blocks. Each paradigm names the blocks it needs, and a block is
added only when a paradigm needs it. A block is whatever lets XPath see further:
over bare git, XPath navigates trees and names blobs; with AVRO, it drills into
the data structures inside the blobs.

## Next: git objects, in memory

- Blobs, trees, commits and refs, content-addressed.
- In-memory, transient repositories: no persistence, no P2P. Every test starts
  from an empty repository.
- A commit is the transaction, the commit graph is the history, and a version
  is a commit hash.
- XPath over git trees, using the settled URI naming scheme. Pointer records;
  selectors always return arrays.
- Tests are lists of normal commands.

## Near

- Mutable working state and transactional writes over the immutable objects.
- The commit log read as a change stream.
- Persistence behind the same objects: filesystem first, then Hyperdrive.
- Instrumentation and audit as data in the repository.

## Further

AVRO (XPath into data structures) · the document paradigm · replication on the
swarm · Hypercore streams · relational and other paradigms.

## Open

- Where the boundaries of the near blocks sit.
