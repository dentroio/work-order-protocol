# WO-103 — Document Local Verification Command

> Illustrative assignment for the fictional Inventory app in the
> [example index](README.md). Its `make verify` target already exists in that
> scenario; it is not a command provided by this documentation repository.

**Status:** Ready
**Priority:** P3
**Effort:** XS
**Owner:** Developer Experience
**Services / Areas:** docs

## Problem

The README does not tell contributors how to run the local verification command
before opening a pull request.

## Decision Context

- Chosen approach: document the existing `make verify` target.
- Alternatives rejected: add a new script or change CI.
- Assumptions: in the fictional project, `make verify` runs lint and tests from
  the repository root, exits 0 on success, and exits nonzero on a failed check.
  Contributors install dependencies using the existing setup section first.
- Open decisions: none within this illustrative assignment.

## What To Build / Fix

Add a short "Verify" section to `README.md`: run `make verify` from the repository
root after the existing dependency setup. Exit 0 means lint and tests passed;
a nonzero exit means the contributor must resolve the reported check before PR.

## Expected Change Surface

- Expected: `README.md`
- Tests: none
- Docs/status: `README.md`, `docs/status.md`.

## Out Of Scope

- Changing CI.
- Adding new scripts.

## Do NOT Change

- The `make verify` target and the checks it runs.
- Existing setup instructions and runtime behavior.

## Acceptance Criteria

1. README names `make verify`, the repository-root working directory, dependency
   setup prerequisite, and the zero/nonzero success and failure conditions.
2. The command agrees with the existing Makefile target and has been exercised
   in the documented environment; actual output is recorded at closeout.
3. No runtime code, scripts, or CI configuration changed.

## Validation Plan

- Automated: run `make verify` from the fictional repository root after setup.
- Manual: inspect the README diff and Makefile target; confirm the documented
  prerequisites, command, and exit-status interpretation match the project.
- Evidence to include: command, environment, exit status, lint/test summary,
  review result, and final changed-file list.

## Execution

- **Branch:** `docs/local-verification-command`
- **Risk tier:** P3
- **Pre-PR / pre-merge gate:** `make verify` plus README/Makefile comparison.
- **Depends on:** none
- **Human verification required:** No
- **Reviewer / approver:** Developer Experience
- **Acceptance decision:** in this fictional scenario, the Developer Experience
  owner accepted the docs-only scope, P3 risk, and validation on 2026-10-08.
- **Project status record:** `docs/status.md`, row WO-103.
- **Other status surfaces to reconcile:** none.

## Closeout

- Verification evidence: pending implementation; no executed check is claimed.
- Review / approval result: pending documentation review; no separate product
  UI verification is required for this P3 assignment.
- Follow-ons filed: record any setup problems separately, or explicitly none.
- Residual risks: pending; note any unverified environment.
- Docs/status updated: pending; README, WO-103, and `docs/status.md`.
- Status surfaces reconciled: pending; no other declared surface.
- Summary metadata reviewed: review last updated, current focus, and blockers.
- Planning-only change? This is a ready assignment, not delivered documentation.

See [the complete closeout walkthrough](complete-closeout.md) for an illustrative
completed snapshot of this same assignment.

