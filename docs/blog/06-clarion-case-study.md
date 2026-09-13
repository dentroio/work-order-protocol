# Case Study: How Clarion Is Built With Work Orders

The Work Order Protocol did not come from a whiteboard.

It came from building Clarion, a production network security product with a
large codebase, multiple services, Docker-baked builds, GitHub CI, coding agents,
and human verification checkpoints.

Clarion is not required to use the protocol. It is the proof that the protocol
can survive real software.

## The Problem

Agents can write code quickly. That is useful only if the work is bounded,
verified, and reviewed in the environment that matters.

Clarion has an extra constraint: editing a source file does not change the
running product until the affected container is rebuilt. An agent that stops at
"tests passed" may have proven a file changed while the product stayed old.

That shaped the process.

## The Work Order

In Clarion, a Work Order is a markdown spec in the repo. It names:

- the problem
- what to build
- what not to touch
- acceptance criteria
- risk tier
- branch and PR expectations
- service rebuilds
- human verification
- closeout and follow-ons

The Work Order is the prompt, but it is more than a prompt. It is the unit of
implementation.

## The Human Checkpoint

For product changes, the implementer rebuilds the affected service, runs smoke
tests, and asks a human to verify the running product before committing.

That is not ceremony. It catches the class of bugs that tests do not see:

- empty states
- stale containers
- misleading UI
- wrong joins
- workflows that typecheck but do not feel true

## The Service Discovery Story

One Clarion feature started as an empty import list. A first Work Order fixed
the lookback window. Once the list populated, the real UX and data-quality issues
became visible: cramped modal, poor names, noisy discovery traffic.

That became the next Work Order.

During review, another better idea appeared: use Clarion's discovered subnets to
classify internal traffic more accurately. That did not get stuffed into the
same pull request. It became a follow-on.

That is the protocol in miniature:

```text
observe -> specify -> implement -> verify -> file the leftover
```

## What Generalizes

You do not need Clarion's stack to use the lesson.

You need:

- a cold-startable unit of work
- explicit scope and out-of-scope
- risk tiers
- validation that matches your runtime
- a human gate for irreversible or judgment-heavy steps
- follow-ons instead of surprise diff expansion

Clarion uses a factory around this. The protocol itself is smaller and portable.

**Next:** [From Work Orders To Agentic Factories](07-work-orders-to-agentic-factories.md)

