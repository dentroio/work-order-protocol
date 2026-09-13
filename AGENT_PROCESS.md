# Agent Process For Work Orders

This file is a generic front door for coding agents working in a repository that
uses Work Orders. Adapt commands to the target project.

## Rules

1. Read the assigned Work Order before editing files.
2. Confirm dependencies and risk tier.
3. Stay inside the Work Order scope.
4. Do not expand adjacent work; file follow-ons.
5. Preserve anything listed under "Do NOT Change."
6. Run the validation plan and quality gate.
7. Ask for human verification when required.
8. Record verification evidence and follow-ons before closeout.

## Implementation Checklist

```text
Read WO
  -> inspect current state
  -> claim or create branch
  -> implement
  -> test
  -> manual verification if required
  -> review
  -> closeout
```

## Never Do

- Do not treat vague acceptance criteria as permission to guess.
- Do not silently skip tests.
- Do not mix unrelated cleanup into the Work Order.
- Do not downgrade risk tier.
- Do not approve your own high-risk spec.
- Do not claim completion without verification evidence.

