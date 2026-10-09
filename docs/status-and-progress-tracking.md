# Status And Progress Tracking

Work Order Protocol does not require a specific project management tool.

A team can use Markdown, GitHub Issues, Linear, Jira, a spreadsheet, a database,
or an automated dashboard. The protocol only requires that status is visible,
versioned or auditable, and kept aligned with the Work Orders it describes.

## The Principle

A Work Order is not complete just because code merged.

It is complete when the work is implemented, verified, reviewed according to its
risk tier, and the project record has been updated.

That project record may be:

- a progress document
- a status board
- an issue tracker
- a release tracker
- a queue file
- a dashboard
- a factory claim record

The format is local. The responsibility is part of the protocol.

## Minimum Status Record

Every project using Work Orders should have one obvious place to answer:

- What work is open?
- What work is in progress?
- What work is under review?
- What work is complete?
- What work is blocked?
- What changed recently?
- What is the current focus or milestone?

For small projects, this can be one Markdown file.

For larger projects, it may be a dashboard backed by issues, PRs, or machine
readable queue files.

## Multiple Status Surfaces

As a project grows, one status record often becomes several surfaces.

That is normal. A team may have:

- a human progress tracker organized by sprint or milestone
- a capability registry organized by product area
- an issue tracker organized by assignment and review
- a machine queue organized by priority and dispatch state
- claim records used by agents or automation
- release notes organized by customer-visible outcome

The protocol can support this, but only if each surface has a declared role.

For every status surface, write down:

- who reads it
- who or what updates it
- whether it is source, projection, or automation state
- when it must be updated
- what other surfaces it must agree with
- what fields are safe for automation to edit
- what fields require human judgment

Without this map, status drift is inevitable. One system says a Work Order is
done, another still says it is open, and a capability registry may not mention
the delivered capability at all.

## Source, Projection, And Automation State

Do not make every status surface equally authoritative.

Classify each surface:

| Surface Type | Purpose | Example |
| --- | --- | --- |
| Source | The canonical record for the Work Order's scope, acceptance, and closeout. | Work Order file, issue, or ticket |
| Project status | Human-facing view of what is open, active, blocked, and recently completed. | Progress document, project board, roadmap tracker |
| Capability status | Human-facing view of shipped capability by product area. | Capability registry, release readiness table |
| Automation state | Machine-facing view used for dispatch, ownership, or workflow. | Queue file, claim file, runner database |
| Derived projection | Generated or periodically reconciled view. | Dashboard, report, rollup |

Automation state can help operate the work, but it should not silently become
the product or project-management story unless the team explicitly chooses that.

## Reconciliation Rule

When a Work Order closes, update every status surface named in the Work Order or
process.

At minimum, reconcile:

- the Work Order source record
- the project-level status record
- any capability or release registry affected by the change
- any automation state used to dispatch or claim the work

If a surface is intentionally not updated, record why in closeout.

This is especially important when automation is added after the project already
has human-facing project-management docs. The new queue or runner state should
serve the protocol; it should not replace existing PM artifacts by accident.

## Row-Level Status

Each Work Order should have a status that is easy to inspect.

Recommended states:

| State | Meaning |
| --- | --- |
| Draft | The problem or scope is still being shaped. |
| Ready | Readiness passed and the human owner's acceptance is recorded; the accepted scope can start when dependencies and ownership permit. |
| Accepted | Optional local alias for Ready, or a separate approval state when the project explicitly defines that distinction. |
| Research | Investigation-only scope; it still needs recorded human acceptance before investigation starts and never authorizes product implementation. |
| In Progress | Someone has claimed or started the work. |
| Review | The implementation is ready for review or verification. |
| Complete | The accepted scope is delivered, verified, reviewed according to risk, and closed out. |
| Blocked | Progress requires a decision, dependency, access, or external event. |
| Deferred | The work is intentionally postponed or replaced. |

Use different labels if your project already has them, but keep the semantics
clear enough that a cold reader can tell what can be picked up next.

In the default lightweight flow, use `Draft -> Ready -> In Progress -> Review
-> Complete`; `Ready` includes human acceptance. The lifecycle guide's
"Accepted" milestone is that decision, not a mandatory extra queue column.
If a project uses separate Ready and Accepted states, document which state
authorizes work and require both readiness and acceptance before starting.
Research describes an investigation-only assignment, not a shortcut around
approval. Its unresolved product questions are the research output, not
permission to ship an unaccepted implementation.

## Summary Metadata

Row-level status is not enough. Most projects also need top-level metadata that
orients a reader before they scan individual Work Orders.

Useful metadata includes:

- last updated date
- current focus or milestone
- release phase
- active blockers
- recently closed work
- source of truth links

When a Work Order changes the status record, the implementer should review both:

- the Work Order's individual status
- the summary metadata that explains the current state of the project

This prevents a common failure mode: rows show recent progress, while the header
or milestone summary still describes an old reality.

## Closeout Requirements

Every completed Work Order should leave closeout evidence.

At minimum, record:

- verification performed
- review or approval result
- docs or status records updated
- follow-on Work Orders or issues filed
- residual risks

Closeout can live in the Work Order, the PR description, the issue tracker, or a
status system. The location can vary. The information should not disappear into
chat history.

## Backstops

Human discipline is useful. Deterministic checks are better.

If a project has CI or scripts, add lightweight backstops for status hygiene:

- fail or warn when a Work Order closes without closeout notes
- fail or warn when a progress/status file changes without summary metadata
  review
- update obvious machine-known fields such as completion date or PR number
- preserve first-writer-wins fields so later bookkeeping does not overwrite the
  real implementation reference
- distinguish planning or filing changes from implementation completion

The protocol does not require automation, but it does recommend it once the
manual rule is clear.

## Planning PRs Are Not Implementation Completion

A Work Order can be created, clarified, split, or reprioritized without being
implemented.

Project tracking should preserve that distinction:

- creating a Work Order means the work exists
- accepting a Work Order means the work is ready
- claiming a Work Order means someone is working on it
- merging the implementation means the work may be complete
- closing out the Work Order means verification and status records caught up

This matters for humans and agents. A planning PR that adds a Work Order should
not accidentally mark that same Work Order complete.

## Portable Checklist

Use this checklist at closeout:

1. Update the Work Order status.
2. Update the central progress/status record.
3. Review summary metadata such as last updated, focus, milestone, and blockers.
4. Record verification evidence.
5. Record follow-ons and residual risks.
6. Confirm the change was implementation work, not only planning or filing work.
