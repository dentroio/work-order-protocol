# WO-103 — Document Local Verification Command

**Status:** Ready
**Priority:** P3
**Effort:** XS
**Owner:** Developer Experience
**Services / Areas:** docs

## Problem

The README does not tell contributors how to run the local verification command
before opening a pull request.

## What To Build / Fix

Add a short "Verify" section to `README.md` with the exact command and expected
success condition.

## Expected Change Surface

- Expected: `README.md`
- Tests: none
- Docs: `README.md`

## Out Of Scope

- Changing CI.
- Adding new scripts.

## Acceptance Criteria

1. README includes the local verification command.
2. No runtime code changed.

## Validation Plan

- Manual: inspect README diff.

## Execution

- **Branch:** `docs/local-verification-command`
- **Risk tier:** P3
- **Pre-PR / pre-merge gate:** none
- **Depends on:** none
- **Human verification required:** No
- **Reviewer / approver:** Developer Experience

