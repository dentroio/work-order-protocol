# Agents

Read `AGENT_PROCESS.md` before starting any implementation task.

Work Orders live in `docs/work_orders/` unless this repo defines another path.
Use the assigned Work Order as the source of truth for scope, acceptance
criteria, risk tier, validation, and closeout.

Default workflow:

1. Read the Work Order and `AGENT_PROCESS.md`.
2. Confirm dependencies and current state.
3. Implement only the scoped change.
4. Run the validation plan and quality gate.
5. Ask for human verification when required.
6. Record follow-ons instead of expanding scope.

Never skip required verification, downgrade risk tier, hardcode secrets, or mix
unrelated cleanup into the Work Order.

