# Base layer — draft

Status: **draft proposal**

## The idea

Mycelium is the repository itself: a common pattern interface on top of a
linked data model. Git, Hypercore, Hyperdrive and other stores sit behind it as
backends. Each store keeps its own authority; Mycelium is the uniform way of
seeing and acting on all of them.

The lowest layer is a **URI-based XPath interface with two modes: mutable and
immutable.**

## Two modes

| | Immutable | Mutable |
|---|---|---|
| Addressed as | URI + position, XPath into the record | URI + optional version, XPath into current or pinned state |
| Operations | append (owner only), read, navigate | read, navigate, write as a transaction |
| Natural backend | Hypercore | Git (on Hyperdrive) |

## Duality

Every write to a mutable node emits a record onto that node's **immutable
change stream**. Consequences:

- **One watch mechanism.** Watching anything means reading an immutable
  stream, whatever the backend.
- **No hidden state.** The history of mutable state is itself immutable,
  addressable data.
- **Pinned links for free.** A version of a mutable node is a position in its
  change stream.

## Rule (proposed)

No mutable node without an immutable history. A store that is mutable without
history (a plain table, a web resource) is admitted only through an adapter
that synthesises the change stream.

## Above the base

Schemas, protocols, merge rules and capabilities live in the layers above, as
metadata on the data — *functionality as metadata*.

## Conformance

The base layer's contract is its conformance suite (`practices/gate.md`): the
immutable family, the mutable family, and the duality property. A new backend
is a new adapter plus a green suite.

## Open

- The exact operation set (draft: resolve, navigate, read, write, append,
  watch, describe).
- Shape of the change record (Kafka-style key, value, offset, timestamp,
  namespaced headers — carried from the Kafka page).
- First adapters: plain filesystem, then git on Hyperdrive, then Hypercore.
