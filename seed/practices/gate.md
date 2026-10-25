# The gate

Status: **agreed direction** (2026-10-25)

## Definition of done

A change is done when the gate returns exit code 0. The gate runs the same way
in a cloud session, in CI and locally.

## Tests are normal commands

A test is a list of the commands a user would type. There is no test
framework: an expectation is itself a command that exits non-zero when it
doesn't hold — a query over state or over the event log.

The verdict stays mechanical. AI reading of the logs adds diagnosis and
explanation; it never decides pass or fail.

## Instrumentation is the evidence

The code is fully instrumented and audited: one structured event stream,
events correlated across operations and peers, recording metadata rather than
private content. A narrative tool turns the stream into readable prose about
what the system did and how it performed.

Instrumentation and narrative are part of the product and stay in operation in
production. Fine-grained configuration tailors them to deployment type, with
profiles as starting points. Configuration changes what is seen, never what
the system does — but the test profile guarantees the events the gate's
commands rely on.

## Requirements and the gate

A requirement is a narrated execution (`requirements.md`). Its concrete values
are projected into checks; the system's own narrative of the run is compared
with the requirement's narrative for diagnosis.

## Growing with the stack

- Each Mycelium block gets its conformance checks: what XPath can address now
  that it couldn't before. Higher blocks never break lower ones.
- The deploy → run → teardown Docker stack joins the gate once nodes exist:
  private bootstrap node, peers, a runner asserting on visible state; topology
  and scenarios as data.
- Runners outside the cloud pick up what the cloud cannot run, and write
  results back.

## Separation of roles

For high-stakes work, tests are written from the requirement by a different
agent than the one implementing, so the work does not grade itself.
