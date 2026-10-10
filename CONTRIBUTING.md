# Contributing

Contributions should make Work Orders easier to understand, adopt, and verify.
Keep changes focused on the protocol, guides, templates, or illustrative examples.

## Propose A Change

Use [GitHub Issues](https://github.com/dentroio/work-order-protocol/issues)
for gaps, contradictions, adoption questions, and proposed improvements.
For larger changes, discuss the intended outcome and scope before drafting a PR.

Include the affected file or section, the problem, the expected result, and a
small example where useful. Explain any change to acceptance, risk, ownership,
verification, or closeout requirements. Remove confidential project details.

## Prepare A Pull Request

Read [AGENT_PROCESS.md](AGENT_PROCESS.md). If using a Work Order, include its
accepted scope and closeout evidence. Keep unrelated cleanup separate.

- Preserve one canonical process; keep tool adapters thin.
- Keep terminology consistent across guides, templates, and examples.
- Label fictional scenarios and simulated evidence clearly. Never present
  example commands or results as checks you actually ran.
- Use project-specific validation only when the example defines that project.
- Do not add credentials, private customer details, or private book manuscript
  material to this public repository.

## Review Checklist

- [ ] Read the changed text for grammar, clarity, and a cold reader's context.
- [ ] Check relative links, linked headings, and fenced code blocks.
- [ ] Compare changed template fields with the quickstart and examples.
- [ ] Preserve recorded human acceptance before implementation, bounded scope,
      risk-based review, honest verification evidence, and status reconciliation.
- [ ] Check adapter filenames and activation guidance against official tool docs
      when changing tool-specific behavior.
- [ ] Run `git diff --check` and report other checks actually performed.
- [ ] State any checks not run and any unresolved decisions in the PR.

This documentation repository does not currently define an executable application
test suite. Commands inside fictional examples are not repository tests.
Maintainer review is required before merging; a submitted PR is not approval.

## Change History And Licensing

Use the PR and commit history to trace changes. Do not promise release dates,
compatibility guarantees, or a support SLA on behalf of the maintainer.

No LICENSE file is currently included. The licensing decision remains with the
repository owner; this guide does not grant additional usage or contribution
rights. Resolve licensing questions with the maintainer before contributing
material whose permissions are uncertain.

For help and safe reporting guidance, see [Support](SUPPORT.md).
