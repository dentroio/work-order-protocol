# WO-101 — Restore List Row Selection

**Status:** Ready
**Priority:** P2
**Effort:** S
**Owner:** Product Engineering
**Services / Areas:** web-ui

## Problem

On `/items`, clicking a table row no longer opens the detail panel. Hover styles
still appear, and console logging confirms the row click handler fires with the
correct item ID. The selected state does not update.

## What To Build / Fix

Investigate `src/pages/ItemsPage.tsx` and the detail panel state flow. Restore
row selection so clicking a row opens the detail panel for that item.

## Expected Change Surface

- Expected: `src/pages/ItemsPage.tsx`
- Tests: `src/pages/ItemsPage.test.tsx`
- Docs: none

## Out Of Scope

- Redesigning the table.
- Adding bulk selection.
- Changing item API responses.

## Do NOT Change

- Existing keyboard navigation behavior.
- Existing row hover style.

## Acceptance Criteria

1. Clicking a row opens the detail panel for that item.
2. Keyboard selection still works.
3. UI tests pass.

## Validation Plan

- Automated: run UI test suite.
- Manual: open `/items`, click a row, confirm the panel opens.

## Execution

- **Branch:** `wo/101-restore-list-row-selection`
- **Risk tier:** P2
- **Pre-PR / pre-merge gate:** `npm test`
- **Depends on:** none
- **Human verification required:** Yes
- **Reviewer / approver:** Product Engineering

