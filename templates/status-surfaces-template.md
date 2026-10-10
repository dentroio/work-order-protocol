# Status Surface Map

Copy this template into your project when more than one status surface exists.
Replace placeholders; remove unused surfaces. A single progress file does not
need an extra map unless it helps clarify ownership.

- Map owner: [person]
- Last reviewed: [date and timezone]
- Work Order source for scope, acceptance, and closeout: [location]
- Authoritative project-status record: [location]
- Local status vocabulary / mapping: [location or definitions]

## Surface Inventory

| Surface / location | Role | Readers | Updater | Update trigger |
| --- | --- | --- | --- | --- |
| [WO directory or tracker] | Source | [readers] | [owner] | [acceptance, scope decision, state change, closeout] |
| [progress file or board] | Project status | [readers] | [owner] | [assignment, state change, closeout] |
| [capability or release registry] | Capability status | [readers] | [owner] | [verified delivery or release change] |
| [queue or claim store] | Automation state | [readers / runtime] | [owner / automation] | [claim, release, dispatch, closeout] |
| [generated dashboard] | Derived projection | [readers] | [generator owner] | [refresh trigger and expected delay] |

Roles describe purpose, not equal authority. Specify field authority below;
do not let a queue or dashboard silently redefine acceptance or completion.

## Per-Surface Contract

Repeat this section for each retained surface:

- Surface: [name and location]
- Authoritative fields: [fields, or none if entirely derived]
- Upstream sources: [locations and fields, or none]
- Must agree with: [other surfaces and shared fields]
- Safe automation edits: [explicit fields and permitted transitions, or none]
- Human decisions: [acceptance, risk, scope, review, delivery approval, etc.]
- Update owner / trigger: [who and when]
- Freshness check: [how readers detect stale data]
- Conflict handling: [who resolves disagreement using which authoritative record]
- Failure / deferral handling: [where to record failure, owner, and next action]

Automation must preserve human decisions and implementation references. Do not
mark work complete from a planning PR, queue exit, or merge event alone.

## Closeout Reconciliation

For each WO, name the affected surfaces in its execution record. At closeout:

1. Record delivery, verification, review, follow-ons, and residual risks in the source.
2. Update project status and review summary metadata.
3. Update affected capability / release records using actual delivery evidence.
4. Reconcile queue and claim state without overwriting source decisions.
5. Refresh or check derived projections against their declared freshness rule.
6. Record any deferred update in closeout with a reason, owner, and next action.

Unmet required delivery, verification, or approval keeps the WO open. A deferred
bookkeeping update must remain visible; it does not turn a pending check into a pass.
