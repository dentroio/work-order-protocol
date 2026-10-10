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
| `AGENT_PROCESS.md` | Humans and explicitly configured tools | Canonical shared process; not a universal auto-loaded filename. |

Different tools may evolve their filenames. The rule is more important than the
exact list: every agent gets a small local adapter pointing at the same canonical
process.

## Verify Activation Before Implementation

Files under `templates/agent-instructions/` are examples, not installed adapters.
Copy only the adapters needed into the target project's actual entry-point
locations, merge with existing instructions, and adjust project paths. Do not
overwrite existing guidance blindly.

Use the checks below in the tool and version you actually run. A file being
present is not proof that its contents reached the agent.

| Tool | Install | Activation check |
| --- | --- | --- |
| Codex | Project-root `AGENTS.md` | Start a fresh run in the intended working directory and ask which instruction files apply. Check global, nested, and `AGENTS.override.md` guidance if the result differs from expectations. See [official discovery and verification guidance](https://learn.chatgpt.com/docs/agent-configuration/agents-md). |
| Claude Code | Project-root `CLAUDE.md` | Use `/memory` to inspect loaded instruction files. Confirm the intended project file appears and ask the agent to read the shared process before work. See [official memory guidance](https://code.claude.com/docs/en/memory). |
| Cursor | `.cursor/rules/agent-process.mdc` with `alwaysApply: true` | Inspect the rule and its status in Customize > Rules. Confirm the rule is active for the intended project. A referenced file is not automatically inlined; require the agent to read the process. See [official rules guidance](https://cursor.com/docs/rules). |
| Gemini CLI | Project-root `GEMINI.md` | Use `/memory show` to inspect loaded context and `/memory reload` after changes. Check configured context filenames if the file is absent. See [official context guidance](https://geminicli.com/docs/cli/gemini-md/). |

Then run this non-editing check in the intended project:

```text
Do not edit files. Read AGENT_PROCESS.md and the assigned Work Order.
Report the process and Work Order paths, recorded human acceptance, risk tier,
dependencies, ownership, validation plan, required approvals, and status records.
Identify any missing information or conflicting instructions before proposing work.
```

Compare the answer with the files; an agent's summary alone is not proof of
automatic loading or future compliance. Record the tool/version, working
directory, installed adapter path, inspection result, and unresolved conflicts
in the project's setup notes. Repeat after changing adapters, tools, or workspace
layout. These are setup checks, not permission to implement the assigned WO.

The shared process must be explicitly read, even when an adapter loads correctly.
Project instructions never override higher-priority policies or permissions.
If guidance conflicts, stop and resolve it with the owner before implementation.

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

