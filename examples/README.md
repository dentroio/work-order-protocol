# Work Order Examples

These are teaching examples for a fictional Inventory app, not assignments to
execute in this documentation repository. Its source files, fixtures, localhost
server, commands, and owners are scenario assumptions. Inspect your own project
and replace those details before accepting a copied Work Order.

| Example | What It Demonstrates |
| --- | --- |
| [UI bug](ui-bug.md) | Bounded repair, protected keyboard behavior, human UI verification. |
| [API contract change](api-contract-change.md) | Explicit pagination contract, visibility checks, coordinated rollout. |
| [Docs-only change](docs-only.md) | Exact verification command, lightweight review, status closeout. |
| [Research spike](research-spike.md) | Accepted investigation with unresolved product decisions, no runtime authority. |
| [Complete closeout walkthrough](complete-closeout.md) | A thin ticket, accepted WO, illustrative evidence, and before/after status. |

The assignment examples are not completed work. Their acceptance decisions are
part of the fictional scenario, and their closeout results remain pending.
The walkthrough shows a completed snapshot of the docs-only assignment; it is
not a second assignment or a real test report. Every simulated result is labeled.

## Scenario Setup

The fictional project has a shared process, a Makefile, and installed development
dependencies. Its existing setup instructions start the seeded app at
`http://localhost:3000`. UI tests run with `npm test` and exit after one run;
`make test` covers API/client regression tests; `make verify` runs lint and tests.
These targets are not provided by Work Order Protocol.

The WO file is the source of scope and closeout. `docs/status.md` is the project's
progress record, with last-updated date, focus, blockers, and a row per WO. The
API example additionally uses `docs/releases.md` for rollout status. There is
no factory queue. All paths in those records refer to the fictional project.

For these examples, Ready means readiness passed and human acceptance is
recorded. Research requires recorded acceptance too, but authorizes only the
investigation. A real human must accept your adapted task; copying an example's
status or fictional approval does not authorize work.

Use the [template](../templates/WO-template.md),
[risk policy](../docs/risk-tiers.md), and
[status definitions](../docs/status-and-progress-tracking.md#row-level-status)
when adapting an example.
