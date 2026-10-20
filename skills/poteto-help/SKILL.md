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

| The user wants to | Skill |
|---|---|
| Do any non-trivial task with rigor | [`$poteto-mode`](../poteto-mode/SKILL.md) |
| Check that the agent understood their goal and the problem before it starts | [`$in-your-own-words`](../in-your-own-words/SKILL.md) |
| Get a deeper rewritten prompt with expert methods and an outside check, without executing its task | [`$sharpen`](../sharpen/SKILL.md) |
| Know how code works now, or where new code should live | [`$how`](../how/SKILL.md) |
| Know why code is shaped this way, or where a number came from | [`$why`](../why/SKILL.md) |
| Understand a change or subsystem, explained plainly | [`$teach`](../teach/SKILL.md) |
| Catch up on their own recent work on a topic | [`$recall`](../recall/SKILL.md) |
| Catch up on changes and list every waiting item with enough context to decide from the reply | [`$ketchup`](../ketchup/SKILL.md) |
| Know what a small diff could break outside itself | [`$blast-radius`](../blast-radius/SKILL.md) |
| Settle types and module shape before code that crosses a function boundary | [`$architect`](../architect/SKILL.md) |
| Get several attempts at one brief, merged into the best one | [`$arena`](../arena/SKILL.md) |
| Run parallel checks over slices, or race workers, with native Codex workers | [`$swarm`](../swarm/SKILL.md) |
| Have independent reviewers inspect a diff and try to break it | [`$interrogate`](../interrogate/SKILL.md) |
| Explicitly request a bug fix with a failing regression test first | [`$tdd`](../tdd/SKILL.md) |
| Apply TypeScript rules to `.ts` or `.tsx` work | [`$typescript-best-practices`](../typescript-best-practices/SKILL.md) |
| Strip comments before review, using a reviewer that didn't write them | [`$no-comments`](../no-comments/SKILL.md) |
| Clean AI tells out of prose | [`$unslop`](../unslop/SKILL.md) |
| Write docs, an RFC, a README, a PR description, or a commit message to a standard | [`$technical-writing`](../technical-writing/SKILL.md) |
| Hear the last reply again in plain words | [`$bro`](../bro/SKILL.md) |
| Give agents a scripted way to drive the app and prove behavior | [`$create-verification-skill`](../create-verification-skill/SKILL.md) |
| Bring a verification skill and its feature map back in line with the app | [`$maintain-verification-skill`](../maintain-verification-skill/SKILL.md) |
| Formally verify a race, invariant, or property that tests rarely reach | [`$create-formal-verification-skill`](../create-formal-verification-skill/SKILL.md) |
| Bring formal verification back in line with changed code and distinguish drift from bugs | [`$maintain-formal-verification-skill`](../maintain-formal-verification-skill/SKILL.md) |
| Vet a performance number before reporting or acting on it | [`$benchmark-checklist`](../benchmark-checklist/SKILL.md) |
| Run a large or cross-cutting change, or one to review after stepping away | [`$figure-it-out`](../figure-it-out/SKILL.md) |
| Keep a decision log during a run, and review it afterward | [`$show-me-your-work`](../show-me-your-work/SKILL.md) |
| Inspect current Codex capabilities and supported model settings | [`$setup-pstack`](../setup-pstack/SKILL.md) |
| Turn their own working habits into a personal mode skill | [`$automate-me`](../automate-me/SKILL.md) |
| Turn what a finished task taught into skill edits | [`$reflect`](../reflect/SKILL.md) |
| Stop agents from repeating the same mistakes in this repo | [`$correct`](../correct/SKILL.md) |
| Build a UI around a supported automation integration | [`$make-bot-ui`](../make-bot-ui/SKILL.md) |
| Find their way around pstack | `$poteto-help` |


Read an unlisted sibling skill's description before recommending it. The `principle-*` directories contain guidance applied where relevant.

Close calls:

- **how** explains current mechanics. **why** investigates historical reasons with citations. **teach** combines them for a plain explanation.
- **arena** compares alternative attempts and synthesizes one artifact. **swarm** covers slices or a declared race and produces one report.
- **architect** settles the design before authorized implementation. A design-only request stops at the design. Add "with checkpoint" when the user wants to approve the design first.
- **interrogate** reviews the selected diff. **blast-radius** traces consequences beyond it and seeks executable evidence of the key safety claim.
- **recall** searches authorized recent history and current state. **ketchup** summarizes only this chat since the user's last message.
- **figure-it-out** designs one substantial run. The Orchestrate playbook coordinates a larger program, subject to the same permissions and host capabilities.

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
