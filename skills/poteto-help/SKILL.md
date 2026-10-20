---
name: "poteto-help"
description: "Guides users through pstack setup, $poteto-mode, and picking the skill, playbook, or principle for a task. Type $poteto-help with a question."
---

Read [the Codex execution contract](../pstack/CODEX.md) before this workflow. It defines supported tools, bounded delegation, shared-checkout ownership, validation, and authorization. Use only capabilities exposed in this session.

# Poteto help

Answer the user's Pstack question and give at most one useful example prompt. A help question is read-only. A request such as "use Pstack to fix this bug" authorizes the work and routes to [poteto-mode](../poteto-mode/SKILL.md).

Read the referenced skill before relying on its details. This is the Codex port; upstream Cursor instructions are historical source material. Link the installed Codex skill or a verified local deliverable, not an upstream page as if it described this port.

## Start in Codex

Invoke a skill through the host's skill picker or with its displayed `$skill-name` syntax. The host may show a plugin namespace. Use that exact exposed name when needed. Do not promise slash commands, Custom Modes, or keybindings from another product.

Use [setup-pstack](../setup-pstack/SKILL.md) for a read-only capability report. Workers follow the shared model policy: only GPT-6.1 Sol or GPT-6 Astra; default Sol Extra High and Astra High; never below High or Ultra. Inheritance requires verified compliant settings. The orchestrator uses native subagents when available, bounded by the actual concurrency limit, and assigns exclusive write ownership. Configuration changes are optional and require the user's request. Setup does not install software or change models automatically.

Setup can point to [create-verification-skill](../create-verification-skill/SKILL.md) when an app harness is missing, and [create-formal-verification-skill](../create-formal-verification-skill/SKILL.md) for a race, invariant, or property that needs deeper verification. If formal verification exists but covered code changed after its recorded sync commit, use [maintain-formal-verification-skill](../maintain-formal-verification-skill/SKILL.md). These are optional next steps, not setup side effects.

A useful first task names the goal, available evidence, constraints, and a check for done. [Prompting guidance](references/prompting.md) and [recipes](references/recipes.md) provide examples. The user does not need to hand-write the skill sequence.

The installed skill catalog and invocation policy control discovery. A skill's availability does not mean it ran. The agent should state when it applies a skill and follow the user's active task across later turns. In a new chat, invoke the workflow again when needed.

## Pick a skill

For a recommendation or a comparison, read [the skill catalog and close calls](references/skill-selection.md). It maps tasks to installed skills and distinguishes overlapping workflows. Read an unlisted sibling skill's description before recommending it.

Use **how** for current mechanics, **why** for historical reasons, and **teach** for a plain explanation combining both. **poteto-mode** routes substantial work. The `principle-*` directories contain guidance applied where relevant.

## Playbooks and principles

Playbooks live inside [poteto-mode](../poteto-mode/SKILL.md). They are not separately registered skills. Describe the work to select one, or name a playbook directly. Examples include investigating a bug, taking over a branch, planning a migration, reviewing a PR, or pausing safely.

A status question stays read-only. A request to babysit a PR allows only the requested work and does not imply merge permission. Commits, pushes, PR creation, merges, issue creation, and messages follow the user's explicit authorization and repository rules.

A request for a plan returns a plan. Use Codex Plan mode when available and appropriate; a skill cannot switch modes by inventing a tool call. A request for a design can use prototypes or **architect** within the requested scope.

Principles explain choices such as proving behavior, keeping ownership clear, and fixing root causes. They do not expand the scope or permissions of the current task.

## Resolve a run problem

| Symptom | Useful next step |
|---|---|
| A skill was not selected | Invoke its displayed name and inspect its description or invocation policy. |
| A model override is unavailable | Use verified compliant inheritance if available; otherwise continue directly and report the delegation limitation. Do not guess a replacement identifier or use a disallowed model or effort. |
| Workers overwrite each other | Stop overlapping writers, preserve their changes, and assign disjoint files or explicit worktrees. |
| A long run reports activity without completion | Restate a falsifiable done check and inspect the actual artifacts. |
| A reply claims success from a build alone | Request evidence from the real user flow, command, stored value, or measurement. |
| Delegation or UI automation is missing | Use a direct or existing CLI path where it meets the task, and state the remaining capability gap. |
| The user wants work to resume later | Use the supported native scheduler after that request. Do not invent a loop command or background daemon. |

Reduce cost by narrowing the scope, reusing evidence, using fewer independent workers, and avoiding redundant review passes. Model changes use the host's supported settings only when requested.

## Customize Pstack

[automate-me](../automate-me/SKILL.md) captures the user's explicit working preferences. [reflect](../reflect/SKILL.md) prepares lessons as focused skill edits. Use the available Codex **skill-creator** for authoring. Propose unrelated skill repairs separately rather than modifying them inside feature work.

For custom subagent behavior, pass the [poteto-agent role brief](../pstack/references/agents/poteto-agent.md) as instructions to a native agent. The file is not an automatic custom-agent registration and does not add tool parameters.

## Reply

Lead with the answer, include one adapted prompt only if useful, and link the relevant Codex skill or reference. Keep the answer short unless the user asks for the full map.
