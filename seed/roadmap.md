# Roadmap

Status: **draft** — revised in spl8, 2026-10-26

Planned PRINCE2-style (`principles.md`): products first, the next stage in
detail and later ones in outline, work managed by exception within
tolerances. A stage is entered when the previous one has proved itself, not
by date.

## The product: capabilities for applications

The near-term product is a set of capabilities on which applications can be
built. Home automation is the first application: it is used to find the
required capabilities, not as the goal itself. Keep it simple.

1. **Nodes on several devices**, including the phone. Each device runs a
   full peer.
2. **P2P between the nodes:** discovery, connection, replication. The spl6
   primitives re-established on current Bare, without `pear run`.
3. **State in git, queried with XPath**, on every node.
4. **Software units:** self-contained components running on a node. Managing
   IoT devices is one thing units do.
5. **Minimal UI capabilities:** every node serves a browser UI locally — on
   the phone from local IP or in-app, on the PC in a browser. The UI never
   depends on reaching another node; P2P carries the rest.

**Prerequisites:** a Docker stack to run several nodes, and a real phone in
the test loop.

## Next

**First stage: research the capabilities.** For each of the five, establish
what exists, what we build, and the risks — by research and by probes.

**Connectivity is tested as part of it.** The options, each a probe with a
phone on mobile data as the hard case:

- Direct holepunching between nodes over the public HyperDHT.
- A home node reachable from outside (public IP, forwarded UDP port,
  dynamic DNS) acting as private bootstrap and blind relay. Fails under
  CGNAT.
- A cheap VPS in the same role, when the home connection is not reachable.
- Cloudflare at the edges only: Tunnel and Access for remote reach of a
  node's UI, Durable Objects as a WebSocket rendezvous, R2 for backups,
  Artifacts (closed beta) for git. Cloudflare cannot host a peer: no UDP in
  Workers, no inbound UDP in Containers, Spectrum UDP is Enterprise only.

Also in this stage: a Bare node with its git store and local HTTP server
running on a phone.

**Then:** capabilities 1–5 built, each as one or more stages; home
automation assembled from them, as the check that none is missing.

## Later

- Mycelium: the layers above the git repository (`design/base-layer.md`).
- Persistence behind git: filesystem, then Hyperdrive.
- Translation between natural language and a unit's internals.
- The working practice moves onto node components.

## Horizon

Multi-paradigm Mycelium · AVRO · Hypercore streams · one owner on several
devices · real networks and relays · circles · interop at the edges.

## Always discussed

Anything touching meaning, the philosophy or a settled commitment; changes to
the principles or working practices; anything irreversible or outward-facing.
