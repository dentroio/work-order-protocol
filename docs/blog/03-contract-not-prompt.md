# A Work Order Is A Contract, Not A Prompt

A prompt asks a model to do something. A Work Order defines a change that must be
made, verified, reviewed, and closed.

That difference matters.

Prompts live in chat. Work Orders live with the code. Prompts can rely on the
last twenty messages. Work Orders have to survive handoff, review, and time.

## The Contract

A strong Work Order has a few load-bearing sections.

`Problem` names the visible pain. It is not the fix.

`Decision Context` records the approach, alternatives rejected, and assumptions.

`What To Build` describes the implementation target.

`Expected Change Surface` says where the work probably belongs.

`Out Of Scope` and `Do NOT Change` keep nearby ideas from expanding the pull
request.

`Acceptance Criteria` define what must be true.

`Validation Plan` defines how to prove it.

`Closeout` records verification, follow-ons, residual risk, and status updates.

## Why Out Of Scope Is Product Strategy

Teams often treat out-of-scope as administrative. It is not.

Out-of-scope is how you say: this idea is real, but it is not this change.

That discipline matters because agents and helpful humans both love adjacent
work. A small fix becomes a redesign. A redesign becomes a new data model. A new
data model becomes a migration. Suddenly no one can review the original change.

Work Orders do not prevent discovery. They route discovery into follow-ons.

## Verification Is Part Of The Work

Acceptance criteria without a validation plan are wishes.

For a UI change, validation may require a browser. For an API change, it may be
a curl response and integration tests. For a migration, it may be an idempotency
check and a rollback plan. For docs, it may be a review of the rendered page.

The right validation is whatever would make "tests passed" an incomplete answer.

## Closeout Feeds The Next Work Order

The closeout section is where a Work Order becomes useful history.

It should answer:

- What evidence proves this was done?
- What follow-ons were filed?
- What risk remains?
- What docs or status changed?

This is the loop. Good Work Orders produce better Work Orders.

**Next:** [Add Work Orders To Any Repo In One Afternoon](04-add-work-orders-to-any-repo.md)

