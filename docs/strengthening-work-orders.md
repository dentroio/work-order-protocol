# Strengthening Work Orders

This document lists concrete upgrades that make Work Orders more reliable for
humans, coding agents, and optional automation.

## Strengthening Goals

Better Work Orders should:

- reduce clarifying questions
- prevent scope expansion
- expose risk early
- make verification concrete
- preserve useful history
- produce clean follow-on work

## Add These Sections

If your current template is minimal, add these sections first.

| Section | Why |
| --- | --- |
| Decision Context | Separates chosen direction from open questions. |
| Expected Change Surface | Bounds likely files, services, tests, and docs. |
| Do NOT Change | Protects invariants and avoids accidental redesign. |
| Validation Plan | Names how acceptance will be proven. |
| Closeout | Captures verification, residual risk, and follow-ons. |

## Add These Process States

Use explicit states so drafts do not look ready:

| State | Meaning |
| --- | --- |
| Draft | Idea is being shaped. |
| Research | Investigate only; do not ship runtime change. |
| Ready | Cold-startable and accepted for implementation. |
| In Progress | Claimed by an implementer. |
| Review | Implementation is ready for review or verification. |
| Complete | Delivered and closed out. |
| Blocked | Cannot proceed without a decision or dependency. |

## Add A Readiness Review

Before implementation, check:

- problem is observable
- outcome is specific
- scope is bounded
- risk tier is correct
- dependencies are explicit
- validation plan exists
- human verification is specified when needed
- follow-on candidates are not mixed into the scope

## Add A Research Spike Type

When the answer is unknown, create a research Work Order instead of a vague
implementation Work Order.

Research output should include:

- findings
- recommendation
- rejected options
- risks
- one or more implementation WOs

## Add A Closeout Requirement

The closeout section should be completed before a Work Order is considered done:

```markdown
## Closeout

- Verification evidence:
- Follow-ons filed:
- Residual risks:
- Docs/status updated:
```

## Add Drift Checks

Before implementation, ask:

- Does the named route, component, module, or API still exist?
- Did a dependency merge change the problem?
- Is the risk tier still correct?
- Are the acceptance criteria still valid?

## Suggested Backport To Existing Processes

For an existing Work Order process, the lowest-friction upgrade is:

1. Add `Decision Context`.
2. Add `Expected Change Surface`.
3. Add `Validation Plan`.
4. Add `Closeout`.
5. Add a readiness checklist before dispatch.

