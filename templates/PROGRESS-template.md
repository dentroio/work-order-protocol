# Project Progress

Copy this template to your chosen project status location, such as
`docs/status.md`. Replace bracketed placeholders and remove unused rows.
Do not treat template rows as accepted or completed work.

## Summary

- Last updated: [date, time, and timezone]
- Updated by: [person or automation]
- Current focus / milestone: [current outcome]
- Release phase: [phase, or not applicable]
- Active blockers: [WO IDs and unblock decisions, or none]
- Recently closed: [WO IDs with closeout links, or none]
- Work Order source: [directory or tracker link]
- Status surface map: [location, or none for a single-surface project]

## Status Rules

Default flow: `Draft -> Ready -> In Progress -> Review -> Complete`.
Ready includes recorded human acceptance of scope, risk, and validation.
Dependencies and exclusive ownership must also permit work to start.
Complete requires delivery, verification, required review, and closeout.
Use Blocked or Deferred when appropriate; record the reason and next action.
If local states differ, replace this paragraph with their explicit mapping.

This record is [the authoritative project-status record / a projection of a
named source]. The linked Work Order remains authoritative for scope,
acceptance, and closeout. Resolve conflicting records before dispatching work.

## Work Orders

| Work Order / source link | Status | Owner | Dependencies / blocker | Next action | Evidence / closeout link |
| --- | --- | --- | --- | --- | --- |
| [WO ID and link] | [actual state] | [owner or unassigned] | [IDs, decision, or none] | [action and responsible person] | [evidence link or pending] |

Include open, active, blocked, review, and completed work. If completed rows move
to an archive, link the archive here: [archive location, or not used].

## Capability And Delivery

| Capability / release | Delivery state | Supporting WOs | Remaining verification / approval |
| --- | --- | --- | --- |
| [capability or release, or remove this table] | [actual delivery state] | [source links] | [pending requirement or none] |

A merged PR is not automatically a shipped capability. Use the project's
delivery definition and keep release status separate when release is pending.

## Recent Changes

| Date | Work Order | Change | Evidence |
| --- | --- | --- | --- |
| [actual date] | [source link] | [planning, acceptance, implementation, or closeout change] | [decision, PR, verification, or closeout link] |

## Update Checklist

- [ ] Update the WO row and its source record without changing accepted scope.
- [ ] Review focus, release phase, blockers, and recently closed work.
- [ ] Record actual verification and review results; skipped checks remain pending.
- [ ] Reconcile other declared status surfaces or record the deferral reason,
      responsible person, and next action in closeout.
- [ ] Update the timestamp and updater only after reviewing the record.
