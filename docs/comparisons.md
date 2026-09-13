# Comparisons

Work Orders overlap with familiar software planning artifacts, but they optimize
for a different handoff: implementation by a cold reader, including a coding
agent.

## Work Orders vs Tickets

Tickets usually identify work. Work Orders specify work.

| Ticket | Work Order |
| --- | --- |
| Often a title plus notes | Complete implementation brief |
| Relies on shared context | Designed for cold start |
| May lack verification | Requires acceptance and validation |
| Often grows in comments | Captures follow-ons separately |

## Work Orders vs User Stories

User stories express value from a user's perspective. Work Orders include that
value, then add implementation boundaries and verification.

Use both if helpful:

```text
As an operator, I want...
```

can live inside the `Problem` section, but it is not enough by itself.

## Work Orders vs RFCs

RFCs decide direction. Work Orders execute bounded slices.

Use an RFC when:

- architecture is unresolved
- multiple teams must align
- the design space is broad

Use a Work Order when:

- the slice is ready to implement
- risk and verification are clear
- scope can be bounded

## Work Orders vs ADRs

ADRs record decisions. Work Orders may reference ADRs.

Do not use a Work Order as the only record for a major architectural decision.

## Work Orders vs Spec-Driven Development

Spec-driven development often moves from requirements to design to tasks. Work
Orders are narrower: one bounded unit of implementation with risk, validation,
and closeout attached.

Work Orders can fit inside a spec-driven process as the dispatchable unit.

## Work Orders vs Agentic Factory

Agentic Factory is one runtime for operating Work Orders.

The Work Order Protocol is independent:

- no dashboard required
- no runner required
- no queue required
- no automation required

A factory helps after the Work Orders are already clear.

