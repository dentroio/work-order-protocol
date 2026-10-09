# A Complete Closeout Walkthrough

This fictional walkthrough follows WO-103 from the
[docs-only assignment](docs-only.md). All dates, people, results, and delivery
records below are illustrative. No Inventory application or `make verify`
command was executed while writing this document. Replace sample evidence with
real output when using the pattern in your own project.

## Start With A Thin Ticket

> Add test instructions to the README.

That leaves the implementer to choose a command, prerequisites, success standard,
and completion record. The fictional owner and implementer inspect the existing
Makefile and setup instructions before accepting a narrower assignment.

## Accept One Bounded Assignment

The owner accepts the following on 2026-10-08. This is a completed snapshot of
WO-103, not an additional task. Its execution contract remains the same as the
ready assignment; closeout records what happened in the fictional scenario.

### WO-103 - Document Local Verification Command

**Status:** Complete (illustrative completed snapshot)
**Priority:** P3
**Effort:** XS
**Owner:** Developer Experience
**Services / Areas:** docs

#### Problem

Contributors cannot find the existing local quality gate in the README. The
fictional Makefile already defines `make verify`, which runs lint and tests.

#### Decision Context

- Chosen approach: document the existing command and its exit status.
- Alternatives rejected: add a script or change CI.
- Assumptions: dependencies are installed through the README's existing setup
  section; `make verify` runs lint and tests once from the repository root.
- Open decisions: none for this assignment.

#### What To Build / Fix

Add a Verify section naming `make verify`, the repository-root working directory,
and the existing setup prerequisite. Explain that exit 0 means lint and tests
passed; a nonzero exit requires investigation before opening a PR.

#### Expected Change Surface

- Expected: `README.md`.
- Tests: no tests added; run the existing quality gate.
- Docs/status: the WO source and `docs/status.md`.

#### Out Of Scope

- New verification scripts, CI changes, or runtime changes.

#### Do NOT Change

- The Makefile target, checks it runs, or existing setup instructions.

#### Acceptance Criteria

1. README names `make verify`, its working directory, dependency prerequisite,
   and zero/nonzero exit interpretation.
2. The command agrees with the Makefile and has been exercised after documented
   setup, with actual results recorded for review.
3. No runtime code, scripts, or CI configuration changes.

#### Validation Plan

- Automated: run `make verify` from the fictional repository root after setup.
- Manual: compare the Verify section with the Makefile and existing setup;
  inspect the changed-file list for scope.
- Evidence to include: command, environment, exit status, lint/test summary,
  reviewer decision, and changed-file list.

#### Execution

- **Branch:** `docs/local-verification-command`.
- **Risk tier:** P3; documentation only.
- **Pre-PR / pre-merge gate:** `make verify` plus README/Makefile comparison.
- **Depends on:** none.
- **Human verification required:** No separate running-product check.
- **Reviewer / approver:** Developer Experience owner.
- **Acceptance decision:** fictional owner accepted scope, P3 risk, and validation
  on 2026-10-08 before implementation.
- **Project status record:** `docs/status.md`, row WO-103.
- **Other status surfaces to reconcile:** none; no capability, release, or queue
  change is needed for this documentation-only assignment.

#### Closeout

- Verification evidence: illustrative record below; in a real project link the
  actual run log and commit verified, not this sample.
- Review / approval result: fictional Developer Experience owner confirmed the
  README matches the Makefile and accepted the documentation diff on 2026-10-09.
- Follow-ons filed: none found in this scenario; no adjacent work was bundled.
- Residual risks: only the documented local environment was checked. Future
  changes to the Makefile must also update the README.
- Docs/status updated: README Verify section, WO-103 closeout, and its row in
  `docs/status.md`.
- Status surfaces reconciled: source and progress record agree; no others declared.
- Summary metadata reviewed: last updated set to 2026-10-09, focus moved to the
  next accepted task, and blockers remain none.
- Planning-only change? No in this scenario: the requested README documentation
  was delivered. This does not claim a runtime feature shipped.

## Claim, Implement, And Review

The implementer confirms the accepted task has no dependency or conflicting
owner, creates the branch, and updates the progress row to In Progress. They add
only the Verify section, run the accepted checks, and record results for review.
The owner reviews and approves the docs change before merge. The WO remains in
Review until delivery and closeout records are reconciled.

Illustrative evidence record, not actual command output:

```text
WO: WO-103
Checked revision: fictional revision docs-verify-1
Environment: fictional contributor laptop, dependencies installed via README setup
Working directory: repository root
Command: make verify
Exit status: 0 (simulated)
Lint result: no reported errors (simulated)
Test result: 24 passed, 0 failed (simulated)
Manual check: Verify section agrees with Makefile; prerequisites and exit semantics match
Changed files: README.md, docs/work_orders/WO-103-local-verification.md, docs/status.md
Reviewer: fictional Developer Experience owner
Delivery: documentation change merged on 2026-10-09 (simulated, not a real PR)
Skipped required checks: none in this fictional scenario
```

In a real closeout, retain the actual output or a durable link, identify the
revision/environment, record failed or unrun checks, and obtain the approvals
required by your risk policy. A copied successful sample proves nothing.

## Reconcile The Project Record

Illustrative `docs/status.md` before implementation:

```markdown
Last updated: 2026-10-08
Current focus: Document the existing local verification command
Blockers: None

| WO | State | Owner | Next Action |
| --- | --- | --- | --- |
| WO-103 | Ready | Developer Experience | Claim the accepted docs-only assignment |
```

Illustrative `docs/status.md` after review, delivery, and closeout:

```markdown
Last updated: 2026-10-09
Current focus: Select the next accepted Work Order
Blockers: None
Recently completed: WO-103; verification command documented and reviewed

| WO | State | Owner | Evidence / Next Action |
| --- | --- | --- | --- |
| WO-103 | Complete | Developer Experience | WO closeout contains validation and review record; no follow-ons |
```

The README is the delivered change. The Work Order preserves the verification
and approval record. The progress document tells the next reader what happened
and where attention goes next. None of these is replaced by a successful merge
alone.

## What This Example Does Not Prove

This walkthrough teaches the record structure, not a runnable application.
It does not validate your commands, establish your risk policy, grant merge
authority, or prove that any product is deployed. For runtime work, name the
actual delivery environment and reconcile capability/release records as needed.
