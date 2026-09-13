# Adoption Levels

Teams can adopt Work Orders gradually. The protocol does not require agents or a
factory.

## Level 1: Human Work Orders

Use Work Orders as better implementation specs.

Add:

- Work Order template
- risk tiers
- validation plan
- closeout notes

Best for:

- small teams
- solo developers
- projects that already use pull requests

## Level 2: Agent-Assisted Work Orders

Add coding agents, but keep the same Work Order process.

Add:

- `AGENT_PROCESS.md`
- `AGENTS.md`
- `CLAUDE.md`
- `GEMINI.md`
- Cursor rule, if using Cursor

Best for:

- teams using Codex, Claude Code, Cursor, Gemini, or similar tools
- repos where agents need clear scope and verification instructions

## Level 3: CI-Gated Work Orders

Make the process harder to skip.

Add checks for:

- tests
- lint
- migration registration
- auth or RBAC invariants
- no hardcoded secrets
- PR title includes WO number
- required docs changed

Best for:

- production systems
- multiple contributors
- security-sensitive repos

## Level 4: Factory-Operated Work Orders

Use a runtime to queue, claim, dispatch, monitor, and merge Work Orders.

Add:

- queue or plan file
- claim files
- dashboard
- agent runner
- PR watchdog
- automated review
- merge policy

Best for:

- many Work Orders
- many agents
- shared runtime environments
- teams that need visibility into agent progress

## Rule

Do not jump to Level 4 to fix unclear specs. Automation amplifies the quality of
the Work Orders you already have.

