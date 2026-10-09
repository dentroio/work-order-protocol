# WO-102 — Add Pagination Metadata To Items API

> Illustrative assignment in the fictional Inventory app described in the
> [example index](README.md). Its contract decisions and acceptance are examples,
> not evidence about a live API or authorization to change one.

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
- Assumptions: the only consumer is the bundled web client in this repository;
  API and client are released together. There are no independently deployed or
  external consumers. If inspection disproves this, stop for a compatibility
  decision and return the assignment to Draft.
- Open decisions: none under those explicit fictional assumptions.

Contract decisions:

- `limit` defaults to 50 and is an integer from 1 through 500.
- `offset` defaults to 0 and is an integer from 0 through 1,000,000.
- Supplied values must contain decimal digits only. Empty, fractional, negative,
  repeated, nonnumeric, and out-of-range values return HTTP 400 with
  `{ "error": "invalid_pagination" }`; do not silently clamp them.
- `meta.total` counts items visible to the authenticated caller before pagination.
  `meta.limit` and `meta.offset` echo the effective values, including defaults.
- Preserve existing ordering: `createdAt` descending, then `id` descending.
- An offset beyond the visible total returns an empty `data` array and the actual
  total, not a 404. Existing item fields and visibility rules are unchanged.
- Replace the response and bundled client together. No backward-compatible
  endpoint is required in this closed fictional deployment. A real project with
  external clients needs an explicitly accepted migration/versioning plan.

## What To Build / Fix

Update `GET /api/items` to return the defined paginated envelope. Update the
bundled caller and tests. Document the contract and deploy API and client as one
release; do not claim compatibility with the former bare-array response.

## Expected Change Surface

- Expected: `src/api/items.ts`, `src/client/items.ts`
- Tests: `tests/api/items.test.ts`
- Docs/status: `docs/api/items.md`, `docs/status.md`, `docs/releases.md`.

## Out Of Scope

- Cursor pagination.
- Sorting changes.
- Filtering changes.

## Do NOT Change

- Existing default item ordering.
- Authorization requirements.

## Acceptance Criteria

1. With 12 visible seeded items, `GET /api/items?limit=10&offset=0` returns
   10 ordered items and `"meta": { "total": 12, "limit": 10, "offset": 0 }`.
2. For the same caller, offset 12 returns
   `{ "data": [], "meta": { "total": 12, "limit": 10, "offset": 12 } }`.
3. Missing parameters apply defaults. Limit 1 and 500 and offset 0 and 1,000,000
   are accepted; invalid values follow the specified HTTP 400 contract.
4. Existing unauthorized-request behavior is preserved. Items hidden from the
   caller never appear in `data` or contribute to `meta.total`.
5. The bundled UI reads the envelope and renders both populated and empty lists.
6. API and client regression tests pass, and the API reference states defaults,
   bounds, invalid-value behavior, total semantics, and rollout constraints.

## Validation Plan

- Automated: `make test`; include contract cases for default, lower/upper bounds,
  invalid and repeated values, empty pages, ordering, visibility, and client use.
- Manual: with the fictional seeded app running at `http://localhost:3000`,
  inspect the signed-in browser request to `/api/items?limit=10&offset=0` and its
  response. Confirm the 12-item fixture and the empty page at offset 12. Check
  populated and empty UI states. Do not paste credentials into review notes.
- Evidence to include: test results, redacted response bodies, caller/fixture
  description, UI verification, and confirmation that consumer inventory still
  supports the coordinated rollout decision.

## Execution

- **Branch:** `wo/102-items-pagination-meta`
- **Risk tier:** P1
- **Pre-PR / pre-merge gate:** `make test`
- **Depends on:** none
- **Human verification required:** Yes
- **Reviewer / approver:** Platform lead
- **Acceptance decision:** in this fictional scenario, the Platform lead accepted
  the contract, coordinated rollout, P1 risk, and validation on 2026-10-08.
- **Project status record:** `docs/status.md`, row WO-102.
- **Other status surfaces to reconcile:** `docs/releases.md`; no factory queue.

## Closeout

- Verification evidence: pending; attach results for every contract case.
- Review / approval result: pending; human verification and merge/release approval
  are required for P1 work.
- Follow-ons filed: capture newly discovered consumers or migration work separately.
- Residual risks: pending; rollout assumptions must be rechecked before release.
- Docs/status updated: pending; API reference and WO-102 progress row.
- Status surfaces reconciled: pending; release record must distinguish merged
  changes from the API/client deployment actually delivered.
- Summary metadata reviewed: review last updated, release phase, and blockers.
- Planning-only change? This is a ready assignment, not a completed API change.

