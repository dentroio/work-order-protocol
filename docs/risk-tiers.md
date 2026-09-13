# Risk Tiers

Risk tiers define how much autonomy the process allows. They should be based on
blast radius, not effort.

## Suggested Tiers

| Tier | Typical work | Human verification | Merge / release authority |
| --- | --- | --- | --- |
| P0 | Auth, secrets, data loss, privacy, payments, destructive operations | Always | Human required |
| P1 | Schema, migrations, API contracts, core workflows, production behavior | Always | Human required |
| P2 | Features, UI, connectors, non-critical fixes, refactors with tests | Usually | May be automated after checks |
| P3 | Docs, examples, PM/status-only changes | Usually no | May be automated after checks |

## Decision Tree

```text
Can this expose, corrupt, delete, or lock people out of important data?
  -> P0

Does this change schema, API contract, core behavior, or production workflow?
  -> P1

Does this change application behavior, UI, integrations, or runtime code?
  -> P2

Is it documentation/status/examples only?
  -> P3
```

## Rules Of Thumb

- Small does not mean low risk.
- Docs-only means no runtime code changed.
- If tiers disagree inside one WO, split it.
- If verification requires product judgment, include a human checkpoint.
- If a coding agent creates the WO, a human should still own risk tier and
  acceptance criteria.

