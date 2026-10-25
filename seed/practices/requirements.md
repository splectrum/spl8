# Requirements as natural-language executions

Status: **agreed in discussion** (2026-10-25)

## The form

A requirement is an execution, talked through in natural language: step by
step, with concrete data, what happens. It is the logical form of the
execution; the software component that performs it is the physical form.

The AI reads the narrated execution and derives what it implies: the data
structures, the schemas, and the functional components that carry out each
step.

## Dry run

Because agents may write natural language, an agent can first carry out the
execution in prose and write down the data that would result. That gives the
expected outcome before any code exists and exposes gaps in the narrative
early.

## Testing

The finished component's run produces its own narrative from its logs. The
requirement's narrative and the system's account of what it actually did are
then both prose about the same execution, and the differences between them are
where diagnosis starts.

The verdict stays mechanical: the concrete values in the narrated execution
are projected, through a component, into structured checks, and those decide
pass or fail.

## Gaps and context

A narrated execution may be incomplete. Context fills the gaps: the design, the
settled conventions, existing components and schemas, earlier executions.

- **Filled gaps are stated**, with where the fill came from.
- **A gap context cannot fill is a real question**, and goes to the human.
- **Repeated fills become conventions**, written into the repository so they
  are context explicitly.

As context grows, requirements can get shorter. How much can be left out is a
rough measure of how much the system already understands.
