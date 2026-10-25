# Design — distillation — draft

Status: **draft proposal**

Prior work sorted into settled, superseded and open. Sources: spl6
(`plan/`, `poc/p2p-docker-dev`, the oracle), spl7 (`plan/`,
`.claude/rules/project-state.md`), splectrum.world engineering pages.

## Settled (carried forward)

**Engineering commitments.** Decentralisation is constitutive; logical over
physical; data first; no hidden state; functionality as metadata; human-AI
collaboration with no central controller.

**Substrate.** Holepunch stack under Bare: HyperDHT, Hyperswarm, protomux,
Hypercore, Hyperdrive. All primitives proven under Bare in spl6.

**Committed languages.** Git (structure, history, transactions), Kafka record
format (data in motion), AVRO (structure — Round 2), URI (identity), XPath
(navigation). Each adopted as a subset.

**Authority split.** Git authoritative for mutable structure; the stream
authoritative for data.

**Naming.** URI segments `[_a-z0-9][a-z0-9]*`; underscore as namespace mount;
files without extension; packed/unpacked indifference.

**XPath.** Pointer records (fully resolved references); selectors always
return arrays.

**Single owner, single writer** per repository / drive.

**Git on Hyperdrive.** isomorphic-git through a Hyperdrive fs adapter — the
Hyperdrive *is* the `.git`. Sparse replication reaches down to index entries:
finer sparsity than git alone. (spl7 phases 2–3)

**Master data view.** Six top-level folders — `packages`, `modules`,
`components`, `config`, `home`, `swarm` — with `swarm/` self-similar.

**Template → install → instance** lifecycle through git forks. (spl7 phase 3)

**Reactive dataflow.** A repo reacts to an append on a subscribed log,
processes, emits to its own log — push, not poll. (spl6 phase 6)

## Superseded or revised

- **Personas as declared capabilities.** Capability is measured by track
  record against the gate, not declared. Personas declare what is *needed*.
- **"Evolve" reinforced by activity.** With AI agents activity is cheap;
  reinforcement needs an explicit fitness signal (tests, verifiers, human
  judgement) and budgets.
- **Neuroscience as grounding.** Kept as inspiration and analogy, not as a
  claim about how current AI works.
- **Phase-per-folder journey.** See `practices/conventions.md`.

## Open

- **The stack** — direction agreed, git objects first: `base-layer.md`.
- **Natural language as authority** — agreed: `natural-language.md`. Still to
  reconcile with the authority split above.
- **The read model** for streams — HAICC triggers depend on it.
- **Cross-owner references** — pinning to commit / sequence.
- **Multi-writer** for shared circle state — owner-mediated merge or Autobase.
- **Bridgehead form** — Docker + Linux FUSE vs Pear's no-install promise.
- **Interop at the edges** — mapping protocols/personas to MCP / A2A at the
  boundary of a circle, without adopting them internally.
- **Round 2** — AVRO, schema-aware navigation, merge rules as schema metadata.
