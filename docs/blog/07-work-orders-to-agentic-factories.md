# From Work Orders To Agentic Factories

Work Orders do not require a factory.

That is worth saying first because it keeps the idea honest. A solo engineer can
use Work Orders. A team can use them with ordinary pull requests. Coding agents
can use them from an IDE.

A factory is what you add when the volume and coordination problem gets bigger.

## What A Factory Adds

An agentic factory can add:

- queueing
- claiming
- worktree creation
- agent dispatch
- status dashboards
- PR watching
- CI review
- merge advice
- post-merge cleanup

Those are operating tools. They are not the protocol.

## Why The Distinction Matters

If the factory is the center of the story, people think they need infrastructure
before they can improve their work.

They do not.

The right order is:

```text
better Work Orders
  -> agent-assisted implementation
    -> CI-gated process
      -> optional factory operation
```

Automation should amplify a process that already works.

## When To Add A Factory

Add a factory when:

- multiple agents may claim work
- there are many Work Orders
- PRs need continuous watching
- stale branches create recurring pain
- status visibility matters
- humans need a queue of verification tasks

Do not add a factory to compensate for vague Work Orders. The result will be a
faster route to the wrong change.

## The Protocol Stays The Same

Whether implemented manually or by a factory, the Work Order still needs:

- problem
- scope
- risk
- validation
- human checkpoint when required
- closeout

The runtime can change. The contract should not.

**Next:** [What To Steal If You Are Not Us](08-what-to-steal.md)

