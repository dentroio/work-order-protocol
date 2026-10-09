# WO-101 — Restore List Row Selection

> Illustrative assignment in the fictional Inventory app described in the
> [example index](README.md). Paths, commands, and acceptance decisions belong
> to that scenario, not to this documentation repository.

**Status:** Ready
**Priority:** P2
**Effort:** S
**Owner:** Product Engineering
**Services / Areas:** web-ui

## Problem

On `/items`, clicking a table row no longer opens the detail panel. Hover styles
still appear, and console logging confirms the row click handler fires with the
correct item ID. The selected state does not update.

## Decision Context

- Chosen approach: repair the existing selection state flow, not the table API.
- Alternatives rejected: replacing the table or adding a new state library.
- Assumptions: local development serves the seeded Inventory app at
  `http://localhost:3000`; `npm test` runs its UI tests once and exits.
- Open decisions: none within this illustrative assignment.

## What To Build / Fix

Investigate `src/pages/ItemsPage.tsx` and the detail panel state flow. Restore
row selection so clicking a row opens the detail panel for that item.

## Expected Change Surface

- Expected: `src/pages/ItemsPage.tsx`
- Tests: `src/pages/ItemsPage.test.tsx`
- Docs/status: `docs/status.md`; no product documentation change.

## Out Of Scope

- Redesigning the table.
- Adding bulk selection.
- Changing item API responses.

## Do NOT Change

- Existing keyboard navigation behavior.
- Existing row hover style.

## Acceptance Criteria

1. Clicking the seeded item `item-101` opens its detail panel and shows its ID.
2. Clicking `item-102` replaces the selected detail with that item's ID.
3. With a row focused, Enter selects it; existing arrow-key navigation remains
   unchanged. A regression test covers both mouse and keyboard selection.
4. The full UI test suite exits successfully.

## Validation Plan

- Automated: `npm test -- src/pages/ItemsPage.test.tsx`, then `npm test`.
- Manual: open `http://localhost:3000/items` with the seeded app running. Click
  `item-101`, then `item-102`; confirm each ID appears in the detail panel.
  Tab to a row, select with Enter, and check arrow-key navigation and hover style.
- Evidence to include: test results, browser/environment and observed IDs,
  verifier's result, and any failed or unrun checks.

## Execution

- **Branch:** `wo/101-restore-list-row-selection`
- **Risk tier:** P2
- **Pre-PR / pre-merge gate:** `npm test`
- **Depends on:** none
- **Human verification required:** Yes
- **Reviewer / approver:** Product Engineering
- **Acceptance decision:** in this fictional scenario, the Product Engineering
  lead accepted this scope, P2 risk, and validation plan on 2026-10-08.
- **Project status record:** `docs/status.md`, row WO-101.
- **Other status surfaces to reconcile:** none; no factory queue is used.

## Closeout

- Verification evidence: pending implementation; no test run is claimed here.
- Review / approval result: pending; human UI verification is required.
- Follow-ons filed: record adjacent issues separately, or explicitly record none.
- Residual risks: pending verification; do not mark Complete before review.
- Docs/status updated: pending; reconcile WO-101 and `docs/status.md` at delivery.
- Status surfaces reconciled: pending; no other declared surface.
- Summary metadata reviewed: review last updated, current focus, and blockers.
- Planning-only change? This is a ready assignment, not completed implementation.

