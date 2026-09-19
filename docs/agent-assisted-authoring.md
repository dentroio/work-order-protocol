# Agent-Assisted Work Order Authoring

You do not have to fill in a Work Order template by yourself.

A coding agent can inspect the repository, gather evidence, identify the likely
change surface, find relevant tests and project instructions, and turn a
conversation into a structured first draft. This is often the easiest way to
start using Work Orders, especially for a solo builder.

The agent drafts the Work Order. The human still owns the intent.

## What The Agent Can Do

An agent can help by:

- locating the code, documentation, tests, and status records related to the
  request
- turning an observation or desired outcome into a clear problem statement
- identifying assumptions and unresolved decisions
- proposing a bounded implementation surface
- suggesting out-of-scope and "Do NOT Change" constraints
- drafting concrete acceptance criteria and a validation plan
- recommending a risk tier for human confirmation
- checking the draft against the cold start test
- writing the draft into the project's Work Order template

The user can begin with ordinary language. A complete specification is not
required before asking the agent for help.

For example:

```text
The saved filters on the reporting dashboard are confusing. They sometimes
come back after a refresh, but not after I sign out and return. Please inspect
the project and help me turn this into a Work Order. Do not implement it yet.
```

## What The Agent Must Not Decide Silently

Repository inspection can reveal how the system currently works. It cannot
decide what the product should do when the answer is not already documented.

The agent should ask for or clearly mark open decisions involving:

- intended user or business outcome
- product behavior with more than one reasonable answer
- acceptable data, security, migration, or operational risk
- scope boundaries that materially change cost or behavior
- approval and human-verification requirements
- priority, timing, or ownership when these are not already established

An agent may recommend answers, but it should label recommendations as
recommendations. It must not convert uncertainty into confident requirements.

## Recommended Authoring Flow

```text
Describe the problem in ordinary language
  -> agent inspects the project and gathers evidence
  -> agent identifies missing decisions
  -> human answers or leaves them explicitly open
  -> agent drafts the Work Order
  -> human reviews intent, scope, risk, and acceptance
  -> Work Order passes the readiness gate
  -> Work Order is accepted for implementation
```

Drafting and implementation are separate actions. Creating a Work Order does
not authorize the agent to change product code, claim the work, or mark it
accepted.

## Reusable Prompt

Use this prompt from an agent that can inspect your repository:

```text
Help me create a Work Order for the problem described below.

You are drafting the Work Order, not implementing it. Do not change product
code, create an implementation branch, or begin the work.

First, read the repository's shared agent/process instructions, Work Order
template, relevant status record, and a few recent accepted Work Orders. Then
inspect the code, tests, documentation, and history needed to understand the
current behavior.

Problem or desired outcome:
[Describe what you observed, what you want to change, and why it matters. Plain
language is fine. Include screenshots, errors, routes, or examples if you have
them.]

Build the draft using the project's Work Order template. The draft must:

- distinguish observed facts from assumptions and recommendations
- state the user or operational impact
- cite concrete repository evidence where available
- define one bounded implementation outcome
- identify the expected change surface without pretending it is guaranteed
- state what is out of scope and what must not change
- propose objective acceptance criteria
- propose automated and manual validation
- recommend a risk tier and explain why
- identify project status or documentation that closeout must update
- capture dependencies and likely follow-on work

Do not invent missing product decisions. Collect unresolved choices under Open
Decisions and ask me focused questions only where my answer would materially
change scope, behavior, risk, or acceptance.

After drafting, perform a readiness review. Report:

1. whether the Work Order passes the cold start test
2. which statements are verified facts
3. which statements are assumptions or recommendations
4. which decisions still require a human
5. whether the work should be split or changed to a research Work Order

Leave the status as Draft until I explicitly accept it.
```

If the agent cannot inspect the repository, it can still organize the user's
notes into a draft. In that case, repository claims, file paths, commands, and
validation steps must be marked for verification by a repo-aware human or
agent.

## Human Review Before Acceptance

Before changing the status from `Draft` to `Accepted`, the human owner should
confirm:

- the problem describes the intended outcome
- the proposed scope is the right-sized unit of work
- out-of-scope and protected behavior are correct
- open product decisions are resolved or intentionally deferred
- the risk tier permits the intended level of agent autonomy
- acceptance criteria test the desired behavior, not merely the proposed code
- validation includes any necessary human observation
- the Work Order names the status and documentation surfaces that closeout must
  reconcile

This review can be brief for low-risk work. The important point is that an
agent-assisted draft becomes accepted work through an explicit human decision,
not because the template happens to be full.

## A Good Division Of Labor

| Human provides or confirms | Agent investigates or drafts |
| --- | --- |
| Why the change matters | Current implementation and evidence |
| Intended product behavior | Likely change surface |
| Scope and priority decisions | Candidate boundaries and splits |
| Risk tolerance and approvals | Risk recommendation and rationale |
| Final acceptance standard | Testable acceptance criteria |
| Authorization to proceed | A cold-start-ready Work Order draft |

Agent-assisted authoring reduces form-filling. It does not remove judgment. The
goal is to make the human's decisions clearer and the agent's research useful,
then preserve both in a durable implementation contract.
