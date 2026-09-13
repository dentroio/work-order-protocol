# Work Order Protocol

A lightweight protocol for turning software intent into verified implementation
by humans, coding agents, or automation.

Work Orders are structured units of work that can be implemented by humans,
coding agents, or an automation runtime. They do not require a factory,
dashboard, queue, or agent runner. Those systems can help operate Work Orders
at scale, but the protocol starts with a simpler promise:

> A cold reader should be able to pick up one Work Order, understand the
> intended change, implement it within bounded scope, prove it works, and leave
> useful evidence behind.

## Why Work Orders

Most software tickets are written for people who share context through meetings,
Slack, memory, or tribal knowledge. That breaks down when work is implemented
later, by a different person, by a coding agent, or across several repos.

A Work Order is different from a ticket because it is designed to be:

- **Dispatchable:** enough information to start without a meeting.
- **Bounded:** clear scope, out-of-scope, and "do not change" constraints.
- **Verifiable:** acceptance criteria are commands, URLs, visible behavior, or
  other concrete checks.
- **Auditable:** risk, owner, branch, verification, and follow-on work are
  visible in version control.
- **Portable:** usable manually, with a coding assistant, or inside an automated
  factory.

## Core Ideas

| Concept | Meaning |
| --- | --- |
| Work Order | One bounded unit of software work. |
| Cold Start Test | A new implementer with no chat history can execute the WO. |
| Creation Gate | A WO is not ready until problem, scope, risk, and verification are clear. |
| Risk Tier | The autonomy and approval budget for the change. |
| Acceptance Criteria | Objective checks proving the change is done. |
| Validation Plan | How implementation will be tested and inspected. |
| Follow-On Capture | New work discovered during implementation is recorded separately. |

## Suggested Repo Shape

```text
docs/
  work_orders/
    WO-001-short-title.md
  work-order-protocol/
    enabling-work-orders.md
    creating-work-orders.md
    implementing-work-orders.md
    risk-tiers.md
templates/
  WO-template.md
  agent-instructions/
    AGENTS.md
    CLAUDE.md
    GEMINI.md
    cursor-agent-process.mdc
examples/
  ui-bug.md
  api-contract-change.md
  docs-only.md
  research-spike.md
AGENT_PROCESS.md
```

Use this structure as-is, or adapt it to your existing project management
system. The protocol does not require any specific directory layout as long as
the Work Orders remain findable, reviewable, and versioned.

## Work Order Lifecycle

```text
Observation
  -> Draft
  -> Readiness Review
  -> Accepted
  -> Claimed / Assigned
  -> Implemented
  -> Verified
  -> Reviewed
  -> Closed
  -> Follow-ons Filed
```

See [Work Order Lifecycle](docs/work-order-lifecycle.md) for the full version.

## What This Is Not

Work Orders are not:

- a generic backlog ticket with a better template
- a replacement for architecture documents
- a license for agents to implement whatever they discover
- tied to any one vendor, model, IDE, CI system, or runtime
- the same thing as an automation factory

An automation factory can run Work Orders. A solo engineer can also run Work
Orders from a terminal and a pull request.

## Start Here

1. Read [Creating Work Orders](docs/creating-work-orders.md).
2. Enable the method in a project with [Enabling Work Orders](docs/enabling-work-orders.md).
3. Copy [the template](templates/WO-template.md).
4. Pick a risk tier from [Risk Tiers](docs/risk-tiers.md).
5. Implement using [Implementing Work Orders](docs/implementing-work-orders.md).
6. Add tool-specific front doors from [Agent Instruction Adapters](docs/agent-instruction-adapters.md).
7. Strengthen your template with [Strengthening Work Orders](docs/strengthening-work-orders.md).
8. Review [What Is Missing From Most WO Processes](docs/process-improvements.md).

## Relationship To Agentic Factory

Agentic Factory is an optional runtime pattern for operating Work Orders with
agent assignment, dashboards, claim files, queue state, CI review, and merge
automation.

The Work Order Protocol is the method. A factory is one implementation path.
