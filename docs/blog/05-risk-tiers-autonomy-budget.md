# Risk Tiers Are An Autonomy Budget

Not all software work deserves the same amount of autonomy.

A typo fix, a dashboard feature, a schema migration, and an authentication change
should not move through the same process. The blast radius is different. The
approval should be different too.

That is what risk tiers are for.

## The Simple Model

| Tier | Use for | Human role |
| --- | --- | --- |
| P0 | Auth, secrets, data loss, privacy, destructive actions | Human approval required |
| P1 | Schema, API contracts, core production workflows | Human approval required |
| P2 | Features, UI, integrations, ordinary runtime fixes | Human verification recommended |
| P3 | Docs and status only | Lightweight review |

The names do not matter. The policy does.

## Risk Is Not Effort

Small changes can be dangerous. Large changes can be low-risk if they are
isolated and well tested.

Risk tiers should answer:

- Could this leak data?
- Could it corrupt or delete data?
- Could it lock users out?
- Could it break an API contract?
- Could it change behavior operators depend on?
- Could automation merge it safely after checks?

## Human Attention Goes Where It Matters

The point of risk tiers is not to slow everything down. It is to stop spending
the same human attention on every change.

Let automation handle lint, tests, formatting, and routine review. Put humans on
product truth, risky decisions, and irreversible actions.

## Agents Need This Boundary

Coding agents are useful inside a bounded change. They should not decide, by
themselves, that an auth change is now safe to auto-merge.

Agents can suggest risk. Humans own risk.

That sentence is small enough to fit on a sticky note and large enough to avoid
real trouble.

**Next:** [Case Study: How Clarion Is Built With Work Orders](06-clarion-case-study.md)

