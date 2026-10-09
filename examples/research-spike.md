# WO-104 — Research Search Backend Options

> Illustrative research assignment for the fictional Inventory app in the
> [example index](README.md). Research status does not authorize product changes;
> the human acceptance below covers the investigation only.

**Status:** Research
**Priority:** P2
**Effort:** M
**Owner:** Platform
**Services / Areas:** research

## Problem

Search latency is increasing as item count grows. The team does not yet know
whether to optimize the current database queries or introduce a dedicated search
backend.

## Decision Context

- Chosen approach: compare alternatives before selecting an implementation.
- Alternatives rejected: immediately install a new search service.
- Assumptions: the fictional team provides a sanitized baseline report with
  100,000 items, p95 search latency of 900 ms, and a target of 300 ms. The planning
  budget is $200/month, excluding staff time. These are scenario inputs, not
  measured results from this repository.
- Open decisions: backend selection, migration approach, and implementation
  scope are outputs of this research, not authority to ship them.

## What To Build / Fix

Do not implement product changes. Compare three options:

- current database with new indexes
- hosted search service
- self-hosted search service

Produce a recommendation and draft follow-on implementation Work Orders.

Timebox the investigation to two working days. Use the provided baseline and
documented vendor/product information. Do not access production data, purchase
services, provision infrastructure, or claim latency improvements without a
reproducible measurement. Mark estimates, unknowns, and information dates.

## Expected Change Surface

- Expected: `docs/research/search-backend-options.md`
- Tests: none
- Docs/status: research note, draft follow-on WOs, and `docs/status.md`.

## Out Of Scope

- Adding a search service.
- Changing production queries.
- Updating UI behavior.

## Do NOT Change

- Production configuration, indexes, secrets, or service accounts.
- Existing search behavior or data handling.

## Acceptance Criteria

1. The note compares all three options against the supplied scale, latency target,
   cost ceiling, operational burden, and data/privacy constraints.
2. Sources and information dates are recorded. Measured results, estimates,
   assumptions, and unresolved questions are clearly separated.
3. The recommendation names a preferred path and rejected alternatives, or
   explains which missing evidence prevents a responsible selection.
4. At least one follow-on WO is drafted, with unresolved implementation decisions
   visible. Drafting it does not authorize implementation.

## Validation Plan

- Automated: no product tests apply; no runtime changes are allowed.
- Manual: the Platform lead checks the comparison, sources, budget assumptions,
  uncertainty, and draft follow-on. Record whether findings are accepted or need
  revision; implementation acceptance is a separate later decision.
- Evidence to include: source/date list, baseline provenance, comparison table,
  time spent, reviewer decision, and links to draft follow-ons.

## Execution

- **Branch:** `research/search-backend-options`
- **Risk tier:** P2
- **Pre-PR / pre-merge gate:** source and comparison checklist above; confirm the
  diff contains only research, draft assignments, and status updates.
- **Depends on:** none
- **Human verification required:** Yes
- **Reviewer / approver:** Platform lead
- **Acceptance decision:** in this fictional scenario, the Platform lead accepted
  this two-day investigation and its P2 review policy on 2026-10-08. Product
  implementation is not accepted.
- **Project status record:** `docs/status.md`, row WO-104; record when research
  starts and who owns it.
- **Other status surfaces to reconcile:** none.

## Closeout

- Verification evidence: pending research; attach findings and sources, not an
  invented benchmark or claim that a backend was deployed.
- Review / approval result: pending architecture review of findings.
- Follow-ons filed: pending; all implementation WOs remain Draft until accepted.
- Residual risks: record unresolved cost, performance, privacy, and migration risks.
- Docs/status updated: pending; research note, WO-104, and `docs/status.md`.
- Status surfaces reconciled: pending; do not mark the product's search capability
  improved merely because research is complete.
- Summary metadata reviewed: review last updated, research focus, and blockers.
- Planning-only change? Yes for product delivery; the accepted research itself
  can close when its findings and review are complete.

