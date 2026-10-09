# Implementing Work Orders

Implementation is the disciplined act of making the Work Order true without
letting the change grow into nearby work.

## Implementation Flow

```text
Read process
  -> Read Work Order
  -> Check dependencies and current state
  -> Create branch or claim ownership
  -> Implement within scope
  -> Verify locally
  -> Ask for required human verification
  -> Run quality gate
  -> Open review
  -> Update status records
  -> Close and capture follow-ons
```

## Before Coding

The implementer should confirm:

- the Work Order has passed readiness review and the human owner's acceptance
  is recorded (`Ready` includes acceptance in the default status scheme)
- dependencies are complete
- the local branch starts from the intended base
- no one else owns the same Work Order
- the risk tier and verification requirements are understood
- the expected touched areas make sense
- the project-level status record is known

## Scope Rule

When new work appears during implementation:

| Discovery | Action |
| --- | --- |
| Required for acceptance criteria | Include it. |
| Same bug, same surface, same risk | Usually include it. |
| Adjacent cleanup | File follow-on. |
| New design decision | Stop for decision or file research WO. |
| Different risk tier | Split or escalate. |

## Verification

Run verification that matches the real delivery environment. Examples:

- `make test`
- `make ci-local`
- `npm test`
- `pytest`
- `curl http://localhost:...`
- browser click-through
- staging deployment check
- migration dry run

The Work Order must name the expected verification before implementation. If
material validation decisions are missing, stop and resolve them with the owner
before coding. Do not choose the success standard after the change is built.
Additional evidence can supplement the accepted plan; material changes to the
plan require the owner's decision and an updated Work Order.

Record checks that could not run and the remaining risk. Do not mark the work
complete until required verification is satisfied, or the responsible human
explicitly accepts a documented exception under the project's policy.

## Status Update

Before a Work Order is considered done, update the project's status record.

This can be a progress document, issue tracker, board, spreadsheet, dashboard,
or queue. The protocol does not require one implementation. It does require the
project record to match reality.

Update or review:

- the Work Order status
- the central progress or project-management record
- affected capability, release, or roadmap records
- automation state such as queues or claim records, if used
- summary metadata such as last updated date, focus, milestone, or blockers
- links to the merged PR, release note, or verification evidence

If the project has multiple status surfaces, use the Work Order's declared
surfaces as the closeout checklist. A machine queue can say what automation is
doing; a capability registry says what the product can do; a progress tracker
says where the project is. Those are related, but they are not automatically the
same artifact.

Do not mark planning-only changes as implementation completion. Creating,
splitting, or editing a Work Order means the Work Order exists; it does not mean
the underlying work has shipped.

## Human Checkpoint

Use a human checkpoint when:

- UI behavior changed
- auth, permissions, billing, or data safety changed
- acceptance depends on product judgment
- the real environment cannot be fully tested by automation

The checkpoint should be specific:

```text
Open <URL>, perform <action>, expect <visible result>.
```

## Closeout

A good closeout records:

- what changed
- how it was verified
- what was intentionally left out
- follow-on WOs or issues
- unresolved risks
- status and project-management records updated

This is where implementation feeds the next cycle of planning.
