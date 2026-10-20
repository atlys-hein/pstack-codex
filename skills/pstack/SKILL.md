---
name: "pstack"
description: "Use Pstack for software implementation, debugging, refactoring, code review and engineering investigations in Codex. Route substantial work through Poteto Mode and delegate independent tasks with native subagents."
license: "MIT"
---

# Pstack for Codex

Read [the Codex execution contract](CODEX.md), then [Poteto Mode](../poteto-mode/SKILL.md) and the complete playbook matching the request. Use [the index](INDEX.md) to find a guide. Read only the relevant principle leaves and supporting references.

Use this workflow for ordinary coding requests without requiring the user to say Pstack. Keep a small local edit small. A question, review or diagnosis stays read-only unless the user also asks for a change.

This skill explicitly requests native subagents for independent research, bounded implementation with separate ownership, and independent verification when those tasks justify delegation. The coordinating agent retains the requested outcome and integrates the actual work. Use [swarm](../swarm/SKILL.md) for coverage and [arena](../arena/SKILL.md) for competing designs. Run tightly coupled or trivial work directly.

The parent selects the playbook. A delegate receives one scoped job and reads [the worker brief](references/agents/poteto-agent.md), the contract, and guidance relevant to that job. It does not start the entire parent workflow again. Further delegation needs a distinct useful subdivision, remaining host capacity and parent permission in its brief.

The package supplies engineering instructions and two small role briefs. Codex supplies tools, authentication, sandboxing and agent execution. Use the current tool schemas and installed capabilities. Never infer that a tool exists because a guide mentions its name.

For installation troubleshooting, use [setup-pstack](../setup-pstack/SKILL.md). Routine coding does not need a plugin audit. [Acceptance checks](ACCEPTANCE.md) distinguish package integrity, installed discovery and observed runtime behavior.
