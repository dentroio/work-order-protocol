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
  -> Close and capture follow-ons
```

## Before Coding

The implementer should confirm:

- the Work Order status is ready
- dependencies are complete
- the local branch starts from the intended base
- no one else owns the same Work Order
- the risk tier and verification requirements are understood
- the expected touched areas make sense

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

The Work Order should name the expected verification. If it does not, the
implementer should add evidence in the PR or closeout notes.

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

This is where implementation feeds the next cycle of planning.

