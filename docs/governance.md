# Governance

Governance answers who may create, approve, implement, and close Work Orders.

Keep governance small at first. The goal is clarity, not bureaucracy.

## Roles

| Role | Responsibility |
| --- | --- |
| Author | Drafts the Work Order. |
| Owner | Accepts priority, risk, and outcome. |
| Implementer | Makes the scoped change. |
| Reviewer | Checks implementation against the WO. |
| Verifier | Confirms the result works in the relevant environment. |

One person can hold multiple roles on low-risk work. High-risk work should split
ownership and implementation.

## Approval Points

| Point | Who should approve |
| --- | --- |
| Risk tier | Owner or responsible engineer |
| Ready state | Owner or reviewer |
| Scope changes | Owner |
| Human verification | Verifier |
| Merge or release | Based on risk tier |

## Risk Ownership

Coding agents should not assign final risk for risky work. They can suggest a
tier, but a human owner should accept it.

## Ready Means Ready

A Work Order should not move to `Ready` until:

- problem is concrete
- scope is bounded
- dependencies are known
- validation is defined
- risk tier is accepted
- open decisions are either resolved or moved to research

In the default flow, the human owner's acceptance of scope, risk, and validation
is recorded before the WO becomes Ready. Projects may use a separate Accepted
state, but must document it and require both gates before work starts. Research
also needs acceptance of the investigation scope; accepting research is not
accepting the eventual product implementation.

## Closure

Only close a Work Order when:

- implementation is delivered
- validation evidence exists
- follow-ons are captured
- residual risks are named
- required docs or status files are updated

