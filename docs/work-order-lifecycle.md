# Work Order Lifecycle

The Work Order lifecycle keeps design, implementation, verification, and
follow-up work separate enough that each step can be trusted.

## 1. Observation

Someone notices a real need:

- a user-visible bug
- a missing feature
- an audit finding
- a failing dependency upgrade
- a security hardening gap
- a refactor needed to unblock future work

The observation is not yet a Work Order. It may still be too vague, too large,
or too uncertain.

## 2. Draft

The author turns the observation into a candidate Work Order. At this stage, it
may still include open questions, rough scope, or possible approaches.

A draft should answer:

- What problem exists?
- Who is affected?
- What evidence shows the problem?
- What outcome would count as fixed?
- What should not be included?

## 3. Readiness Review

Before dispatch, the Work Order must pass the cold start test:

> Could a capable implementer with no prior conversation read this and make the
> intended change without inventing major product or architecture decisions?

Readiness requires:

- problem is concrete
- scope is bounded
- risk tier is assigned
- acceptance criteria are checkable
- validation plan is plausible
- dependencies are explicit
- owner or reviewer is known
- unresolved questions are either answered or marked as research-only

## 4. Accepted

An accepted Work Order is ready to be implemented when capacity exists. It may
sit in a backlog, milestone, issue tracker, local folder, or factory queue.

Acceptance does not mean someone has started. It means the work is shaped.

## 5. Claimed / Assigned

The implementer takes ownership for this unit of work. In a lightweight process,
this can be a branch or issue assignment. In a more automated setup, it may be a
claim file, status board, or queue entry.

The important rule is simple: only one implementer should believe they own the
same Work Order at the same time.

Claiming should update whichever status record the project uses. That may be an
issue assignment, board column, Markdown row, queue item, or dashboard state.

## 6. Implemented

Implementation follows the Work Order. New discoveries are handled carefully:

- Same concern, necessary to satisfy acceptance criteria: include it.
- Adjacent concern, tempting cleanup, or new design: file a follow-on.
- Blocking ambiguity: stop and ask for a decision.

## 7. Verified

Verification proves the change works in the environment that matters.

That might mean:

- unit tests
- integration tests
- local app click-through
- staging deployment
- API curl output
- screenshot evidence
- device lab validation
- migration dry run

"Tests passed" is not enough when the real risk is runtime behavior.

## 8. Reviewed

Review checks the implementation against:

- Work Order scope
- acceptance criteria
- risk tier
- security and data safety
- maintainability
- testing evidence
- docs impact

Review can be human, automated, or both. Risk determines how much human approval
is required.

## 9. Closed

The Work Order is closed only when:

- implementation is merged or otherwise delivered
- verification evidence exists
- the Work Order status is updated
- the project-level status record is updated
- summary metadata such as last updated date, focus, milestone, or blockers has
  been reviewed
- follow-on work is captured
- any required docs are updated

Closing a planning change is different from closing implementation work. A PR
or issue that creates a Work Order should not by itself mark that Work Order
complete unless it also delivered the accepted scope.

## 10. Follow-Ons Filed

Good Work Orders produce good follow-ons. During implementation, teams learn
things. The discipline is not to ignore them; it is to avoid hiding them inside
the current change.

Follow-ons preserve reviewability and keep the original Work Order honest.
