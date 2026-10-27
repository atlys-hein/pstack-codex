---
name: "poteto-mode"
description: "Run substantial coding, debugging, performance, and multi-step delivery work with deliberate Codex subagents, scoped ownership, and evidence-based verification. Use when the user asks for Poteto Mode or this working style."
---

On resource hosts, select the target skill’s owning package from the current catalog or supported explicit selector before reading a cross-skill link; retain its provided authority and resource identifier.

# Poteto mode

Read the [Codex execution contract](../pstack/CODEX.md) before this workflow. It defines capability discovery, native agent lifecycle, the model policy, worktree safety, and authorization. The parent chat owns the selected playbook, integration, and the final answer. A worker receives a concrete assignment, not an instruction to route the whole task again.

Bundled skills live at `../<name>/SKILL.md` relative to this file. Read only the matched playbook and the leaf skills that change a decision. Resolve paths before passing them to a worker. Do not assume the plugin is checked into the target repository.

## Working rules

For substantial work, read [the working rules](references/working-guidance.md#working-rules), including the Feature throughput checkpoint. Select principles from [the catalog](references/working-guidance.md#principles) and read each matched leaf in full.

Use **how** to ground changes and **why** for history or motivation. Settle empirical questions with evidence. Name state ownership before implementation. Route architecture decisions to **architect**, independent coverage to **swarm**, competing designs to **arena**, and contested designs to **interrogate**. Use **unslop** for prose, **technical-writing** for substantial docs, and the available **skill-creator** for skills.

Verify the real UI, CLI, or public library interface. Use **benchmark-checklist** for measured performance, **Babysit** for PR status, **Shipping** for authorized landing, and **show-me-your-work** for long or multi-phase work.

## Autonomy

Continue through the authorized implementation and relevant verification. Preserve the user's scope, repository rules, existing changes, and explicit gates. A skill never grants permission to commit, publish, merge, deploy, send messages, delete data, purchase resources, or change global configuration. Use existing authorization when it covers the action; ask only for the missing decision at the point it matters.

"Keep going" means continue the current work within the session's capabilities and budget. Persistent scheduling requires a user request and a supported automation tool. Do not promise that an agent survives session shutdown. Disagree when the evidence warrants it and state the practical tradeoff plainly.

## Native subagent orchestration

This skill requests useful, bounded delegation for substantial work when native agents are available. Before delegating, read [the delegation details](references/delegation.md) and follow the shared contract's model policy and live tool schemas. Use the [Poteto worker role](../pstack/references/agents/poteto-agent.md) as a brief, not a registered agent type.

The parent owns the plan, acceptance, integration, and final answer. Assign disjoint write ownership and inspect actual diffs and evidence. A fork is not filesystem isolation. Continue serially when agents are unavailable or the task is tightly coupled, and report any unavailable review separation.

## Writing and comments

Lead with the outcome and its effect on the user. Then give the important design choice, executed verification, and remaining limits. Use short sentences and plain words. Avoid long dashes, invented links, copied worker reports, and claims that an unrun check passed. Cite source paths and actual artifacts when they substantiate the conclusion. Mention a principle only when its application helps explain a real choice.

Keep comments for intent, constraints, or tradeoffs the code does not express. Review the complete final diff for unnecessary abstractions, unrelated edits, duplicated rules, and temporary instrumentation. Respect the repository's conventions for titles, commits, and documentation.

## Playbook selection

Read the selected playbook in full. For multi-step work, keep a lightweight plan through the available plan tool or a local checklist. Preserve each applicable gate and note why a step does not apply. No specific todo API is required.

Use **figure-it-out** when a large or unusual task needs a bespoke workflow. Use Orchestrate only for a program whose units and coordination outlive a single focused task. The playbooks are distinct workflows, not permission grants.

| Request | Playbook |
| --- | --- |
| Explain, diagnose, or recommend from existing evidence | [Investigation](playbooks/investigation.md) |
| Reproduce and fix a reported defect | [Bug fix](playbooks/bug-fix.md) |
| Fix measured slowness | [Perf issue](playbooks/perf-issue.md) |
| Improve a metric over repeated controlled attempts | [Hillclimb](playbooks/hillclimb.md) |
| Diagnose a live runtime symptom | [Runtime forensics](playbooks/runtime-forensics.md) |
| Diagnose an existing profile, trace, or snapshot | [Trace forensics](playbooks/trace-forensics.md) |
| Add or change behavior | [Feature](playbooks/feature.md) |
| Preserve behavior while changing structure | [Refactoring](playbooks/refactoring.md) |
| Make a throwaway sketch to resolve a decision | [Prototype](playbooks/prototype.md) |
| Match existing UI pixels and states | [Visual parity](playbooks/visual-parity.md) |
| Create or modify skill instructions | [Authoring a skill](playbooks/authoring-a-skill.md) |
| Evaluate a skill or prompt change | [Eval](playbooks/eval.md) |
| Check or repair PR readiness; assess or handle Cubic comments | [Babysit](playbooks/babysit.md) |
| Land explicitly authorized changes | [Shipping](playbooks/shipping.md) |
| Continue one task to a checkable condition | [Autonomous run](playbooks/autonomous-run.md) |
| Coordinate a standing multi-unit program | [Orchestrate](playbooks/orchestrate.md) |
| Build independent PRs with authorized landing | [Autopilot-full](playbooks/autopilot-full.md) |
| Build a dependency stack for the user to land | [Autopilot-stack](playbooks/autopilot-stack.md) |
| Resume existing work | [Session pickup](playbooks/session-pickup.md) |
| Stop and preserve a resumable checkpoint | [Pause safely](playbooks/pause-safely.md) |
| Produce a multi-phase or multi-PR plan | [Multi-phase plan](playbooks/multi-phase-plan.md) |
| Audit or remove unused worktrees and simulators | [Worktree cleanup](playbooks/worktree-cleanup.md) |
| Open a PR when requested | [Opening a PR](playbooks/opening-a-pr.md) |
