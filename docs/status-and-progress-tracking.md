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

## Row-Level Status

Each Work Order should have a status that is easy to inspect.

Recommended states:

| State | Meaning |
| --- | --- |
| Draft | The problem or scope is still being shaped. |
| Ready | The Work Order passed readiness review and can be implemented. |
| In Progress | Someone has claimed or started the work. |
| Review | The implementation is ready for review or verification. |
| Complete | The work is merged or accepted, verified, and closed out. |
| Blocked | Progress requires a decision, dependency, access, or external event. |
| Deferred | The work is intentionally postponed or replaced. |

Use different labels if your project already has them, but keep the semantics
clear enough that a cold reader can tell what can be picked up next.

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

