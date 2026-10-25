# The gate — draft

Status: **draft proposal**

## Definition of done

A change is done when **one command returns exit code 0**. The command runs
everywhere the same way: a cloud session, CI, a laptop, a VPS.

The gate produces **evidence** as well as a verdict — logs and a report
attached to the run — so the human can review what happened without
re-running anything. Evidence supports the verdict; it does not replace it.

## Two layers

### 1. Conformance suites

The spl6 oracle — 73 full-chain tests, no mocking, each suite returning
`{ pass, message }` — defined correct Mycelium behaviour over TCP. It becomes
the starting conformance baseline, ported to Mycelium on the P2P substrate.

For the base layer (see `design/base-layer.md`) the suite has two families,
one per mode, plus one property linking them:

- **Immutable:** append by owner, read by position, navigate by XPath.
- **Mutable:** read, navigate, transactional write, read at pinned version.
- **Duality:** replaying a mutable node's change stream reproduces its state.

Every backend adapter must pass the same suite.

### 2. The swarm stack

A self-contained **deploy → run → teardown** cycle with Docker Compose:

- a private bootstrap node (never the public DHT),
- N peer nodes (the bridgehead image),
- a runner that drives a scenario and asserts on visible data state through
  the peers' interfaces — *no hidden state* applied to testing.

Topology and scenarios are **data** (files), not code, so the same images and
the same test run on loopback, across Docker networks, or across hosts.

Deterministic where possible: pinned image digests, fresh volumes per run,
fixed seeds. Logs collected before teardown, scrubbed before commit.

The spl6 p2p-docker-dev phases become **scenarios with assertions**: peers
connect, the drive replicates, an instance forks, an instance is visible to
other peers.

### Degraded networks (later)

Partitions by disconnecting containers from networks; latency and loss with
`tc netem`; NAT by placing peers behind small router containers — bringing
hole-punching into the self-contained stack.

## Where it runs

- **Cloud session / CI:** everything up to convergence on a private testnet.
- **Real-network tier:** hole-punching across real networks, long-running
  swarms — own machine, a VPS, or a scheduled CI job. To be confirmed by probe.

## Separation of roles

For high-stakes work, tests are written from the spec by a different agent
than the one implementing, so the work does not grade itself.

## Open

- Whether a compose swarm with peer discovery runs inside a cloud session
  (first probe — `probes/`).
- Which oracle suites port directly and which need rework.
- The command name and report format.
