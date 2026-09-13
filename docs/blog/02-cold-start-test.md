# The Cold Start Test

A Work Order is ready when someone can implement it without the conversation
that created it.

That someone might be a teammate in another time zone. It might be you, three
weeks from now. Increasingly, it might be a coding agent with no useful memory
of the meeting where the work was shaped.

The cold start test asks:

> Can a capable implementer read this artifact, understand the change, avoid
> adjacent work, verify the result, and close it cleanly?

If the answer is no, the Work Order is not ready.

## The Bad Version

```text
The import flow is confusing. Clean it up.
```

This will produce activity. It will not reliably produce the intended product.

The implementer has to invent:

- which import flow
- what confusing means
- whether this is UX, API, data quality, or copy
- what behavior should not change
- how to verify done

The missing context becomes part of the implementation. That is backwards.

## The Better Version

```text
On /services/import, the candidate list is hidden in a narrow modal even though
operators need to compare many rows before importing. Move the review workflow
to a full-width tab. Keep the existing import API unchanged. Do not change how
candidates are discovered.

Acceptance:
1. /services?view=discovery opens the full-width review tab.
2. Existing import action still calls POST /api/services/import.
3. Candidate discovery logic is unchanged.
4. Browser verification confirms operators can compare rows without horizontal
   scrolling.
```

Now the implementer has a box. The box does not solve every design problem. It
does something more useful: it prevents accidental work from masquerading as
helpfulness.

## What The Test Requires

A cold-startable Work Order includes:

- an observable problem
- the intended outcome
- the likely change surface
- out-of-scope work
- hard invariants
- acceptance criteria
- validation plan
- risk tier
- closeout expectations

This is not paperwork for its own sake. Each field prevents a specific failure.

## Why Agents Make This More Important

Human implementers often stop when the spec is vague. Agents tend to continue.

That makes the quality of the input more important, not less. The Work Order is
the place where product judgment, risk, and verification are made explicit before
the fast part begins.

If a Work Order fails the cold start test, do not dispatch it. Rewrite it,
split it, or turn it into a research Work Order.

**Next:** [A Work Order Is A Contract, Not A Prompt](03-contract-not-prompt.md)

