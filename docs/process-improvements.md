# What Is Missing From Most Work Order Processes

This document tracks improvements that teams should consider adding to their
own Work Order process. It is intentionally framework-level, not tied to any
single product.

## 1. Creation Readiness Gate

Many teams define how to implement a Work Order but not how a Work Order becomes
ready. Add a readiness review before dispatch.

Minimum gate:

- concrete problem
- bounded scope
- out-of-scope section
- risk tier
- acceptance criteria
- validation plan
- dependency check
- owner or reviewer

## 2. Draft vs Ready vs Research

Not every idea should be implemented. Use explicit states:

- `draft`: still being shaped
- `research`: investigate and recommend, no product change
- `ready`: implementable
- `blocked`: cannot proceed without external decision
- `accepted`: ready and prioritized

This prevents half-designed ideas from becoming code.

## 3. Decision Context

Agents and future humans need to know which choices are already made. Add a
small section for:

- chosen approach
- alternatives rejected
- assumptions
- decisions still open

## 4. Expected Change Surface

Add expected touched areas:

```markdown
## Expected Change Surface
- frontend route: `src/pages/...`
- API route: `services/...`
- tests: `tests/...`

## Do NOT Change
- authentication model
- unrelated navigation
- database schema
```

This is especially valuable for agent implementation.

## 5. Validation Plan Separate From Acceptance

Acceptance criteria define what must be true. Validation plan defines how to
prove it.

Example:

```markdown
## Acceptance Criteria
1. Users can export a CSV from the Reports page.

## Validation Plan
- Unit test CSV formatter
- Browser check Reports -> Export
- Confirm downloaded CSV headers
```

## 6. Follow-On Capture

Require a closeout note or PR section:

- follow-ons created
- follow-ons intentionally not created
- deferred scope
- known residual risk

This keeps "while I was in there" work from bloating the current change.

## 7. Drift Checks

Work Orders can go stale. Before implementation, check:

- the named files still exist
- dependencies are merged
- acceptance criteria still match product behavior
- risk tier still makes sense

## 8. Framework Independence

Keep the method independent from any runtime.

Good wording:

> Work Orders can be implemented manually, by a coding agent, or by an automated
> factory.

Avoid implying:

> A Work Order must move through the factory.

The factory is optional. The Work Order is the portable artifact.

## 9. Closeout Quality

Closing a Work Order should produce a useful historical record:

- summary
- verification evidence
- changed files or systems
- follow-ons
- docs impact

This is what makes the next Work Order better.

## Suggested Additions To Existing Processes

If your process already has Work Orders, the highest-value additions are:

1. Add a creation readiness checklist.
2. Add explicit draft / research / ready states.
3. Add Decision Context.
4. Add Expected Change Surface and Do NOT Change.
5. Add Validation Plan.
6. Add required Follow-On Capture at closeout.

