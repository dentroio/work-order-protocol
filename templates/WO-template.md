# WO-NNN — Short Descriptive Title

**Status:** Draft | Research | Ready | Accepted | In Progress | Review | Complete | Blocked
**Priority:** P0 | P1 | P2 | P3
**Effort:** XS | S | M | L | XL
**Owner:** human or team
**Services / Areas:** service, package, app, docs, none

Choose one status, not the whole list. In the default flow, Ready means the
human owner accepted the scope, risk, and validation plan. Record who accepted
it and when. A Research assignment also requires acceptance and authorizes
investigation only. See [status definitions](../docs/status-and-progress-tracking.md#row-level-status).
Priority is urgency; risk tier is blast radius and approval policy, even when
both use P0-P3 labels.
When copying this template to a different directory or tracker, adapt links and
paths to your project; the status link above points into this companion repo.

## Problem

Describe the visible problem, missing capability, or reason this work exists.
Include evidence: routes, file paths, logs, screenshots, customer report, failing
test, or observed behavior.

Do not hide the solution in this section.

## Decision Context

- Chosen approach:
- Alternatives rejected:
- Assumptions:
- Open decisions:

Omit or keep short if the work is straightforward.

## What To Build / Fix

Describe the concrete implementation:

- files or areas likely touched
- API contracts
- data model changes
- UI behavior
- function or class expectations
- docs required

## Expected Change Surface

- Expected:
- Tests:
- Docs/status:

## Out Of Scope

- Tempting adjacent work that should not be included.
- Follow-on ideas that deserve separate Work Orders.

## Do NOT Change

- Hard invariants.
- Existing behavior that must be preserved.
- Areas that are intentionally excluded.

## Acceptance Criteria

1. Concrete, checkable outcome.
2. Command, URL, visible result, or artifact.
3. Quality gate passes.

## Validation Plan

- Automated:
- Manual:
- Evidence to include:

## Execution

- **Branch:** `wo/NNN-short-name`
- **Risk tier:** P0 | P1 | P2 | P3
- **Pre-PR / pre-merge gate:** command or checklist
- **Depends on:** none | WO-NNN
- **Human verification required:** Yes / No
- **Reviewer / approver:** person, team, or role
- **Acceptance decision:** human owner, date, and accepted scope/validation; pending for Draft
- **Project status record:** file, issue, board, dashboard, or other source of truth
- **Other status surfaces to reconcile:** capability registry, release tracker, automation queue, claim file, none

## Closeout

- Verification evidence:
- Review / approval result:
- Follow-ons filed:
- Residual risks:
- Docs/status updated:
- Status surfaces reconciled:
- Summary metadata reviewed:
- Planning-only change? Yes / No
