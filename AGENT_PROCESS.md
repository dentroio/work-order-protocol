# Agent Process For Work Orders

This file is a generic front door for coding agents working in a repository that
uses Work Orders. Adapt commands to the target project.

## When Asked To Draft A Work Order

Drafting is not implementation authorization.

1. Read the project process, template, status record, and relevant existing WOs.
2. Inspect enough code, tests, and documentation to ground the draft in evidence.
3. Separate verified facts from assumptions and recommendations.
4. Ask for or mark open decisions that materially affect behavior, scope, risk,
   or acceptance.
5. Recommend a risk tier, but do not silently reduce or finalize risk.
6. Leave the Work Order in `Draft` until a human accepts it.
7. Do not edit product code, create an implementation branch, or claim the WO
   unless the user separately authorizes implementation.

See `docs/agent-assisted-authoring.md` for the full authoring flow and reusable
prompt.

## Rules

1. Read the assigned Work Order before editing files.
2. Confirm recorded human acceptance, dependencies, ownership, and risk tier.
3. Stay inside the Work Order scope.
4. Do not expand adjacent work; file follow-ons.
5. Preserve anything listed under "Do NOT Change."
6. Run the validation plan and quality gate.
7. Ask for human verification when required.
8. Update the project status record and review summary metadata.
9. Record verification evidence and follow-ons before closeout.

## Implementation Checklist

```text
Read WO
  -> confirm readiness and recorded human acceptance
  -> inspect current state
  -> claim or create branch
  -> implement
  -> test
  -> manual verification if required
  -> review
  -> update status record
  -> closeout
```

## Never Do

- Do not treat vague acceptance criteria as permission to guess.
- Do not silently skip tests.
- Do not mix unrelated cleanup into the Work Order.
- Do not downgrade risk tier.
- Do not approve your own high-risk spec.
- Do not claim completion without verification evidence.
- Do not begin implementation with unresolved material validation decisions.
- Do not let planning-only Work Order changes count as implementation completion.
