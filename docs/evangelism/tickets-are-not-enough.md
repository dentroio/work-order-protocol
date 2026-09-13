# Tickets Are Not Enough For Coding Agents

Most software tickets were written for humans who already share context.

They assume the implementer was in the meeting, remembers the Slack thread, knows
which file is cursed, understands the product tradeoff, and can ask the same
person three clarifying questions before lunch.

Coding agents do not have that context. New teammates often do not either.

That is the gap the Work Order Protocol is trying to close.

## Tickets Identify Work

A ticket might say:

```text
Fix the dashboard filters.
```

That identifies a problem area. It does not define the work.

Which dashboard? Which filters? What is broken? What behavior should stay the
same? How do we prove it works? Is this a UI bug, API bug, schema issue, or
product decision?

A senior engineer can often recover the missing context. A coding agent will
usually guess.

Sometimes the guess is good. Sometimes it creates a polished pull request for
the wrong problem.

## Work Orders Make Work Executable

A Work Order says:

- what problem is visible
- where the likely change surface is
- what to build
- what not to change
- how to verify it
- what risk tier applies
- what follow-on work should be captured separately

The test is simple:

> Could a capable implementer with no chat history pick this up and make the
> intended change?

We call that the cold start test.

## Why This Matters Now

AI coding tools made implementation cheaper to start. They did not make bad
specification cheaper to fix.

In fact, vague work gets more expensive when agents are involved because agents
are fast enough to build the wrong thing before anyone notices.

Work Orders are a small discipline for slowing down at the right moment: before
implementation.

## No Factory Required

You do not need a new tool to start.

Create a `docs/work_orders/` folder. Copy a template. Write one focused Work
Order. Implement it on a branch. Run the validation plan. Close it with evidence
and follow-ons.

That is Level 1.

Later, you can add coding agents, CI checks, dashboards, or an automation
factory. Those are useful, but they are not the protocol.

The protocol is the Work Order: a bounded unit of intent that can become a
verified change.

