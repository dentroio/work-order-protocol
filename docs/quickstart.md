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

This is the one file every human and coding agent should follow.

## 5. Choose A Status Record

Use whatever your project already trusts: a Markdown file, issue tracker, board,
spreadsheet, dashboard, or queue.

The only requirement is that open, active, blocked, review, and complete Work
Orders have one visible source of truth.

## 6. Implement The Work Order

Use a branch:

```text
wo/001-first-change
```

Then:

1. Read the WO.
2. Make only the scoped change.
3. Run the validation plan.
4. Capture follow-ons instead of expanding scope.
5. Update the status record.
6. Open a pull request or merge through your normal process.

## 7. Close It

Before marking the WO complete, fill in:

- verification evidence
- follow-ons filed
- residual risks
- docs/status updated
- summary metadata reviewed, if your status record has it

That closeout is what makes the next Work Order better.
