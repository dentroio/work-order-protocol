# WO-104 — Research Search Backend Options

**Status:** Research
**Priority:** P2
**Effort:** M
**Owner:** Platform
**Services / Areas:** research

## Problem

Search latency is increasing as item count grows. The team does not yet know
whether to optimize the current database queries or introduce a dedicated search
backend.

## What To Build / Fix

Do not implement product changes. Compare three options:

- current database with new indexes
- hosted search service
- self-hosted search service

Produce a recommendation and draft follow-on implementation Work Orders.

## Expected Change Surface

- Expected: `docs/research/search-backend-options.md`
- Tests: none
- Docs: research note

## Out Of Scope

- Adding a search service.
- Changing production queries.
- Updating UI behavior.

## Acceptance Criteria

1. Research note compares cost, complexity, latency, and operational risk.
2. Recommendation names one preferred path.
3. At least one implementation WO is drafted.

## Validation Plan

- Manual: architecture reviewer reads the note and approves a follow-on path.

## Execution

- **Branch:** `research/search-backend-options`
- **Risk tier:** P2
- **Pre-PR / pre-merge gate:** none
- **Depends on:** none
- **Human verification required:** Yes
- **Reviewer / approver:** Platform lead

