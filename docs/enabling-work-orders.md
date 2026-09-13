# Enabling Work Orders In A Project

This guide enables Work Orders without requiring an automation factory.

You can use it in a normal repository with humans, coding agents, pull requests,
and your existing CI. A factory, dashboard, or runner can be added later, but it
is not required.

## Minimum Viable Setup

Add these files or equivalents:

```text
AGENT_PROCESS.md
docs/work_orders/
templates/WO-template.md
```

Optional agent front doors:

```text
AGENTS.md
CLAUDE.md
GEMINI.md
.cursor/rules/agent-process.mdc
```

## Step 1. Choose A Work Order Directory

Default:

```text
docs/work_orders/
```

If your organization already has project management docs, use:

```text
docs/project_management/work_orders/
```

The exact path matters less than consistency. Every contributor and agent should
know where accepted Work Orders live.

## Step 2. Add The Template

Copy:

```text
templates/WO-template.md
```

into your repo, or adapt it into your issue tracker.

Keep these sections:

- Problem
- Decision Context
- What To Build / Fix
- Expected Change Surface
- Out Of Scope
- Do NOT Change
- Acceptance Criteria
- Validation Plan
- Execution
- Closeout

## Step 3. Define Risk Tiers

Use the default P0-P3 tiers or map them to your own language.

The important decision is not the names. It is who can approve what:

| Tier | Meaning |
| --- | --- |
| P0 | Security, secrets, data loss, destructive actions. Human approval required. |
| P1 | Schema, APIs, core production behavior. Human approval required. |
| P2 | Product behavior, UI, connectors, ordinary fixes. Human verification recommended. |
| P3 | Docs and status only. Lightweight review. |

Write this in `AGENT_PROCESS.md` so agents and humans share one rule.

## Step 4. Define The Quality Gate

Name the command or checklist that proves the project still works.

Examples:

```bash
make ci-local
npm test
pytest
cargo test
go test ./...
```

If there is no single command yet, define a temporary checklist and file a Work
Order to create one.

## Step 5. Define Human Verification

Some work needs a person to look at the running product. This is true even
without a factory.

Use exact verification language:

```text
Open http://localhost:3000/items, click a row, expect the detail panel to open.
```

Avoid:

```text
Make sure it works.
```

## Step 6. Add Agent Instruction Adapters

If coding agents will work in the repo, add thin adapter files:

- `AGENTS.md`
- `CLAUDE.md`
- `GEMINI.md`
- `.cursor/rules/agent-process.mdc`

Each should point to `AGENT_PROCESS.md`. Do not duplicate the full process into
each adapter.

## Step 7. Use A Lightweight Manual Flow

For a project without a factory, a normal flow is:

```text
Create WO
  -> review readiness
  -> create branch
  -> implement
  -> run quality gate
  -> perform human verification when required
  -> open PR
  -> review
  -> merge
  -> update WO closeout
```

Branch naming is optional but useful:

```text
wo/NNN-short-title
```

## Step 8. Add Claiming Only If Needed

Claim files are optional outside a factory. They are useful when multiple agents
or developers may pick up work concurrently.

Lightweight alternatives:

- issue assignment
- draft PR
- branch naming
- status field in the WO

Use claim files when you need machine-readable ownership:

```text
docs/work_orders/runs/WO-NNN.json
```

## Step 9. Close The Loop

At closeout, record:

- verification evidence
- follow-ons filed
- residual risks
- docs updated

This is how the process gets stronger over time.

## Adoption Checklist

Use this checklist to enable Work Orders in an existing repo:

1. Add a Work Order directory.
2. Add a WO template.
3. Add `AGENT_PROCESS.md`.
4. Define risk tiers.
5. Define quality gate.
6. Define human verification policy.
7. Add agent adapter files if using coding agents.
8. Create one small example WO.
9. Implement it manually or with an agent.
10. Update the process based on what was missing.

## When To Add A Factory Later

Add automation only after the manual process is clear.

A factory helps when you need:

- WO queueing
- autonomous dispatch
- status dashboards
- claim files
- PR watching
- merge automation
- cross-agent coordination

Do not use a factory to compensate for unclear Work Orders. Automation makes a
strong process faster and a weak process louder.

