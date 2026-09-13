# Add Work Orders To Any Repo In One Afternoon

You do not need a new project management tool to start using Work Orders.

You need one directory, one template, one shared process file, and the discipline
to verify work before calling it done.

## Step 1: Add A Directory

```text
docs/work_orders/
```

Keep accepted Work Orders somewhere visible and versioned. If your repo already
has project management docs, use that structure.

## Step 2: Add A Template

Start with the template in this repo:

```text
templates/WO-template.md
```

For the first adoption pass, do not customize too much. The sections are there
because they prevent common failures.

## Step 3: Add A Process File

Add:

```text
AGENT_PROCESS.md
```

This file tells humans and agents how work moves through the repo.

If you use coding agents, add thin front doors:

```text
AGENTS.md
CLAUDE.md
GEMINI.md
.cursor/rules/agent-process.mdc
```

Each should point back to the same process file. Do not maintain four different
versions of the truth.

## Step 4: Pick A First Work Order

Choose something small and visible:

- README verification section
- UI copy fix
- focused bug
- small API response improvement

Avoid your thorniest architectural problem. The first Work Order should prove
the process, not stress every edge case.

## Step 5: Implement And Close

Use your normal branch and PR process.

The important part is closeout:

- validation evidence
- human verification when required
- follow-ons captured
- residual risks named

That is enough for Level 1 adoption.

## Then Add More

Once Work Orders feel natural, add:

- agent instruction adapters
- CI checks
- PR title conventions
- claim files
- queueing
- dashboards
- factory automation

But start with the artifact. A factory cannot rescue vague work.

**Next:** [Risk Tiers Are An Autonomy Budget](05-risk-tiers-autonomy-budget.md)

