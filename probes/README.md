# Probes

Small grounding experiments. Each probe is a folder with a `README.md` (the
question and the answer), a re-runnable `run.sh`, and a committed, scrubbed
`run.log`. Probes answer a question needed to agree a practice or a design —
they are not engineering.

## Planned

| Probe | Question |
|---|---|
| `cloud-swarm` | Does a Docker Compose swarm — private bootstrap node plus peers that discover each other and replicate — run inside a Claude Code cloud session? |
| `real-network` | Can a scheduled CI job join the public DHT and hole-punch to a peer elsewhere? |
