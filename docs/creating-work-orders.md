# Creating Work Orders

Creation quality determines implementation quality. The most important Work
Order work happens before anyone writes code.

## Creation Sources

Work Orders can come from:

- human product observation
- customer report
- bug investigation
- architecture review
- security audit
- dependency failure
- operational incident
- AI-generated draft reviewed by a human
- follow-on discovered during another Work Order

The source does not matter as much as the readiness gate.

## Creation Flow

```text
Observe
  -> Capture evidence
  -> Decide whether this is one unit of work
  -> Draft the Work Order
  -> Assign risk and owner
  -> Review readiness
  -> Accept, split, reject, or mark research-only
```

## Readiness Checklist

A Work Order is ready when it answers these questions:

| Question | Why it matters |
| --- | --- |
| What is visibly wrong or missing? | Prevents vague implementation. |
| Who cares? | Keeps outcome tied to user or operator value. |
| Where is the likely change surface? | Avoids repo-wide wandering. |
| What is explicitly out of scope? | Prevents scope expansion. |
| What must not change? | Protects invariants and existing behavior. |
| What proves it is done? | Replaces vibes with checks. |
| What risk tier applies? | Determines approval and verification. |
| What dependencies exist? | Prevents race conditions and stacked confusion. |
| What docs or status need updating? | Keeps the system of record honest. |

## Decision Context

Add a short decision section when the implementation involves judgment.

Use it for:

- why this approach was selected
- alternatives rejected
- assumptions the implementer may test
- decisions the implementer is not allowed to revisit

Avoid turning this section into an architecture essay. If the design is large,
write a separate design doc and have the Work Order point to it.

## Research-Only Work Orders

If the team does not yet know what should be built, write a research Work Order.

Research WOs should produce:

- findings
- recommendation
- risks
- proposed implementation Work Orders

They should not quietly ship product changes.

## Splitting Work

Split a Work Order when:

- acceptance criteria mix unrelated outcomes
- different services or owners are involved
- risk tiers differ
- implementation would produce a large, hard-to-review diff
- one part can safely ship without another

A good split creates parallelism and cleaner review.

## Creation Anti-Patterns

| Anti-pattern | Better |
| --- | --- |
| "Fix the dashboard" | Name the route, visible symptom, and expected behavior. |
| Solution appears before problem | Explain symptom first, then chosen approach. |
| Many unrelated bullets | Split into multiple WOs. |
| "Make it better" acceptance | Use commands, URLs, screenshots, or observed outcomes. |
| No out-of-scope section | Name tempting extras explicitly. |
| Agent writes and approves its own risky spec | Human owns risk and acceptance. |

