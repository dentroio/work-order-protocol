# Quickstart

This is the smallest useful Work Order setup.

## 1. Add A Work Order Directory

```text
docs/work_orders/
```

## 2. Copy The Template

Copy:

```text
templates/WO-template.md
```

Use it to create:

```text
docs/work_orders/WO-001-first-change.md
```

## 3. Fill The Minimum Fields

For your first Work Order, fill in:

- Problem
- What To Build / Fix
- Out Of Scope
- Do NOT Change
- Acceptance Criteria
- Validation Plan
- Execution

Keep the first one small. A README fix, UI copy change, or focused bug is ideal.

You do not have to complete the template alone. Ask a coding agent to inspect
the repository and draft the Work Order from your description of the problem.
You provide or confirm the intent, scope, risk, and acceptance standard; the
agent can gather evidence and structure the draft.

Use the prompt and review flow in [Agent-Assisted Work Order
Authoring](agent-assisted-authoring.md). Drafting is not authorization to
implement: keep the Work Order in `Draft` until a human accepts it.

## 4. Add A Shared Process File

Copy or adapt:

```text
AGENT_PROCESS.md
```

This is the shared project process. If using a coding agent, configure its
[tool-specific entry point](agent-instruction-adapters.md) to read it;
AGENT_PROCESS.md is not a universal automatically loaded filename. Project
instructions do not override higher-priority tool policies or permissions.

## 5. Choose A Status Record

Use whatever your project already trusts: a Markdown file, issue tracker, board,
spreadsheet, dashboard, or queue.

The only requirement is that open, active, blocked, review, and complete Work
Orders have one visible source of truth.

For a Markdown record, copy the [progress template](../templates/PROGRESS-template.md)
to `docs/status.md`. If several records must agree, adapt the
[status surface map](../templates/status-surfaces-template.md) too.

Write the chosen location into the WO's `Project status record` field. Name
any capability, release, or automation records that must also change at closeout,
or explicitly write `none`. See [Status And Progress
Tracking](status-and-progress-tracking.md).

## 6. Review Readiness And Accept The Work

Before implementation, the human owner confirms:

- the problem and intended outcome are clear
- scope, exclusions, and protected behavior are explicit
- the [risk tier](risk-tiers.md), validation plan, and quality gate are defined
- required human verification and the reviewer/approver are named
- material product decisions are resolved, or the scope is research-only
- dependencies and status records are named

Record the acceptance decision and mark the WO `Ready`, or the equivalent
accepted state in your project. In this guide, `Ready` includes human acceptance;
if your project separates readiness from acceptance, require both before work
starts. See [Governance](governance.md).

Do not begin just because an agent filled the template. Resolve missing material
validation decisions before coding; use a research WO when the outcome is an
investigation rather than a product change.

## 7. Implement The Work Order

Use a branch:

```text
wo/001-first-change
```

Then:

1. Re-read the accepted WO and process; confirm the files and assumptions are
   still current, dependencies are complete, and no one else owns the work.
2. Claim or assign the WO, create the branch, and update the status record to
   `In Progress`.
3. Make only the scoped change. Capture adjacent work as follow-ons; ask the
   owner before changing scope or required validation.
4. Run the accepted validation plan and quality gate. Record results and any
   checks that could not run. Do not treat skipped checks as passes.
5. Obtain required human verification, open review, and record the review and
   merge/release approvals required by the risk tier.
6. Deliver through the project's normal process. Keep the WO open if required
   delivery or verification is still pending.

## 8. Close It

Before marking the WO complete, fill in:

- verification evidence
- review and approval results
- follow-ons filed
- residual risks
- docs/status updated
- other declared status surfaces reconciled, or a recorded reason for deferral
- summary metadata reviewed, if your status record has it

That closeout is what makes the next Work Order better.

Read the [complete closeout walkthrough](../examples/complete-closeout.md) to
see the assignment, illustrative evidence, and before/after progress record
together. The [example index](../examples/README.md) also includes UI, API,
docs-only, and research assignments.
