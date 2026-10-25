# Git in node repos

Status: **agreed direction** (2026-10-25) — for the P2P phases, not yet
implemented

This is git as a Mycelium component inside a node, owning its own repository.
It is separate from git as a tool used by a cloud agent on GitHub, whose
constraints don't shape this design.

## Base

- Git objects first — blob, tree, commit, ref — in memory, then persisted on
  Hyperdrive. spl7 proved isomorphic-git on Hyperdrive: the Hyperdrive *is* the
  `.git`.
- Single writer per repository.

## Transactions

- **The tree is state; the commit is the transaction.** The commit message
  carries the executed requests and their responses, in natural language with
  embedded blocks.
- **Queued requests are state.** They live in the tree or in refs under the
  node's control, and leave state when executed.
- **Requests from other peers live in their own repos.** The node watches what
  it subscribes to, executes, and its transaction commit references the
  request by URI and commit. The requester owns the request; the executor owns
  the transaction.
- **Annotations after the fact** attach as notes, without rewriting history.

## Mounts

A node in one repo's tree can point to another repo at a pinned commit,
resolved transparently and fetched sparsely on access.

- **History is layered, not duplicated.** The linked repo holds the history of
  its content; the mounting repo holds the history of its view — where the
  mount sits, which version it points to, and why it moved.
- **Writing through a mount** is two steps in a safe order: commit in the
  linked repo, then move the pointer. If the linked repo has another owner,
  the write becomes a proposal to that owner.
- Subtree-style copying does not fit Mycelium: it erases owner boundaries.
  A split — history viewed through one prefix — survives as a read-only
  projection.

## Multi-writer

Each writer's branch lives in that writer's own repo. `main` is formed from
them:

- **Owner-mediated:** the owner merges; `main` keeps a single writer.
- **Derived:** no one writes `main`; every peer computes it with the same
  deterministic merge. Commit metadata is derived from the inputs, and conflict
  resolution follows merge rules held as schema metadata.

The derived form serves one owner on several devices.

## Open

- isomorphic-git underneath, or a fully custom implementation.
- How repos replicate between peers.
- The commit log as the change stream, in detail.
