# Work Order Protocol

A lightweight protocol for turning software intent into verified implementation.

Work Orders are for teams that want clearer software work in the age of coding
agents. They turn a vague ticket into a bounded, verifiable implementation
contract that a human, an AI coding agent, or an automation runtime can execute.

They do not require a factory, dashboard, queue, or agent runner. Those systems
can help operate Work Orders at scale, but the protocol starts with a simpler
promise:

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

## 5-Minute Quickstart

1. Copy [templates/WO-template.md](templates/WO-template.md) into your repo.
2. Create `docs/work_orders/WO-001-first-change.md`.
3. Fill in `Problem`, `What To Build`, `Out Of Scope`, `Acceptance Criteria`,
   `Validation Plan`, and `Execution`.
4. Add [AGENT_PROCESS.md](AGENT_PROCESS.md) so humans and agents share the rules.
5. Implement the WO on a branch.
6. Run the validation plan.
7. Close with verification evidence and follow-ons.

For a fuller setup, read [Enabling Work Orders](docs/enabling-work-orders.md).

## Core Ideas

| Concept | Meaning |
| --- | --- |
| Work Order | One bounded unit of software work. |
| Cold Start Test | A new implementer with no chat history can execute the WO. |
| Creation Gate | A WO is not ready until problem, scope, risk, and verification are clear. |
| Risk Tier | The autonomy and approval budget for the change. |
| Acceptance Criteria | Objective checks proving the change is done. |
| Validation Plan | How implementation will be tested and inspected. |
| Status Record | The project-level place where WO state, focus, blockers, and recent change are visible. |
| Follow-On Capture | New work discovered during implementation is recorded separately. |

## Adoption Levels

| Level | Name | What you add |
| --- | --- | --- |
| 1 | Human Work Orders | Template, risk tiers, validation, closeout. |
| 2 | Agent-Assisted Work Orders | Add `AGENT_PROCESS.md` and thin agent adapters. |
| 3 | CI-Gated Work Orders | Add checks that enforce tests, security, and process invariants. |
| 4 | Factory-Operated Work Orders | Add queueing, claiming, dashboards, dispatch, and merge automation. |

Start at Level 1. Do not add automation until the Work Orders themselves are
clear.

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

## Project Status

The protocol is independent of any project management system, but it does expect
status to be real.

Each project should have one obvious place to track open, active, blocked,
review, and complete Work Orders. That can be a Markdown progress file, GitHub
Issues, Jira, Linear, a spreadsheet, a dashboard, or a factory queue.

When a Work Order is closed, update both the individual Work Order status and
the project-level status record. If the project has summary metadata such as
last updated date, current focus, release phase, or blockers, review those too.

See [Status And Progress Tracking](docs/status-and-progress-tracking.md).

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

1. [Quickstart](docs/quickstart.md)
2. [Enabling Work Orders](docs/enabling-work-orders.md)
3. [Creating Work Orders](docs/creating-work-orders.md)
4. [Implementing Work Orders](docs/implementing-work-orders.md)
5. [Risk Tiers](docs/risk-tiers.md)
6. [Status And Progress Tracking](docs/status-and-progress-tracking.md)
7. [Agent Instruction Adapters](docs/agent-instruction-adapters.md)
8. [Adoption Levels](docs/adoption-levels.md)
9. [Comparisons](docs/comparisons.md)
10. [Governance](docs/governance.md)
11. [Strengthening Work Orders](docs/strengthening-work-orders.md)

## Relationship To Agentic Factory

Agentic Factory is an optional runtime pattern for operating Work Orders with
agent assignment, dashboards, claim files, queue state, CI review, and merge
automation.

The Work Order Protocol is the method. A factory is one implementation path.

## Evangelize

The [evangelism guide](docs/evangelism/blog-plan.md) includes blog themes,
audiences, titles, and a first-post draft for explaining Work Orders publicly.
The polished [blog series](docs/blog/README.md) starts with the standalone
protocol, continues into an example case study, and then explains the optional
factory path.
