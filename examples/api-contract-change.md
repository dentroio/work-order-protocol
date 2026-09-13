# WO-102 — Add Pagination Metadata To Items API

**Status:** Ready
**Priority:** P1
**Effort:** M
**Owner:** Platform
**Services / Areas:** api

## Problem

`GET /api/items` returns a bare array, so clients cannot render total counts or
pagination controls without fetching every item.

## Decision Context

- Chosen approach: return `{ "data": [...], "meta": { "total": N, "limit": N, "offset": N } }`.
- Alternatives rejected: response headers only, because current clients consume JSON bodies.
- Assumptions: existing clients can be updated in the same change.
- Open decisions: none.

## What To Build / Fix

Update `GET /api/items` to return a paginated envelope. Update callers and tests.

## Expected Change Surface

- Expected: `src/api/items.ts`, `src/client/items.ts`
- Tests: `tests/api/items.test.ts`
- Docs: API reference

## Out Of Scope

- Cursor pagination.
- Sorting changes.
- Filtering changes.

## Do NOT Change

- Existing default item ordering.
- Authorization requirements.

## Acceptance Criteria

1. `GET /api/items?limit=10&offset=0` returns `data` and `meta`.
2. Empty result is `{ "data": [], "meta": ... }`.
3. Existing UI renders without error.
4. API tests pass.

## Validation Plan

- Automated: API tests.
- Manual: curl the endpoint and paste response shape in review.

## Execution

- **Branch:** `wo/102-items-pagination-meta`
- **Risk tier:** P1
- **Pre-PR / pre-merge gate:** `make test`
- **Depends on:** none
- **Human verification required:** Yes
- **Reviewer / approver:** Platform lead

