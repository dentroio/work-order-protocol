# Agent Instruction Adapters

Agent instruction files are part of a practical Work Order setup, but they are
not the core framework. Treat them as adapters.

The core framework is:

- Work Order template
- creation readiness gate
- lifecycle
- risk tiers
- implementation and validation process

Agent instruction adapters are the thin files that tell each coding tool to read
the shared process and follow Work Orders.

## Recommended Pattern

Keep one canonical process file:

```text
AGENT_PROCESS.md
```

Then add thin front-door files for each tool:

```text
AGENTS.md
CLAUDE.md
GEMINI.md
.cursor/rules/agent-process.mdc
```

Each front door should say:

1. Read `AGENT_PROCESS.md` before implementation.
2. Work Orders live in the chosen WO directory.
3. Stay in scope.
4. Run the project quality gate.
5. Ask for human verification when required.

Do not copy the full process into every adapter. Duplication creates drift.

## Known Front Doors

| File | Common consumer | Purpose |
| --- | --- | --- |
| `AGENTS.md` | Codex and other agentic coding tools | Generic repo instructions. |
| `CLAUDE.md` | Claude Code | Claude-specific entry point. |
| `.cursor/rules/agent-process.mdc` | Cursor | Always-applied Cursor rule. |
| `GEMINI.md` | Gemini CLI / Google-oriented agent workflows | Gemini-specific entry point when supported by the workflow. |
| `AGENT_PROCESS.md` | All tools | Canonical shared process. |

Different tools may evolve their filenames. The rule is more important than the
exact list: every agent gets a small local adapter pointing at the same canonical
process.

## Adapter Responsibilities

Adapters should include:

- the process file to read
- the Work Order directory
- the default verify command
- the local UI or API verification target, if relevant
- a reminder not to commit or merge before required human verification
- any tool-specific quirks

Adapters should not include:

- product secrets
- long duplicated process text
- stale examples from another product
- risky permissions that only one tool happens to support
- instructions that conflict with `AGENT_PROCESS.md`

## Drift Control

When changing the process:

1. Update `AGENT_PROCESS.md`.
2. Check each adapter still points to it.
3. Avoid changing all adapters unless the front-door wording itself changed.
4. If an adapter must diverge for a tool, explain why in that adapter.

## Minimal Adapter Examples

See:

- [AGENTS.md](../templates/agent-instructions/AGENTS.md)
- [CLAUDE.md](../templates/agent-instructions/CLAUDE.md)
- [GEMINI.md](../templates/agent-instructions/GEMINI.md)
- [cursor-agent-process.mdc](../templates/agent-instructions/cursor-agent-process.mdc)

