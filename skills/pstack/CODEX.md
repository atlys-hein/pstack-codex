# Codex execution contract

This contract governs the Pstack port's workflows and role briefs. It adapts Poteto's engineering methods to Codex, using the current session's tools. User scope, applicable AGENTS.md files, higher-priority instructions and runtime permissions govern every action.

## Scope and tool ownership

A plugin provides skills and resources. It does not create native subagent tools, grant access, install connectors, change model settings or expand authorization. Reading a playbook never authorizes commits, pushes, PR creation, merge, deployment, messages, scheduling, deletion or unrelated cleanup. Reuse authorization already given and complete authorized preparation before asking for a missing decision.

Use local Git for working-tree operations. Prefer an available GitHub connector for remote PR operations, with an installed CLI as fallback. Read a PR's current head before reviewing or acting on it. Follow the user's rules for drafts, messages and external writes. Keep read-only status requests read-only.

Use the skills catalog paths or resource identifiers provided by the host. On a filesystem host, resolve relative links from the file being read. On a resource host, each skill can be a separate package: select the package that owns the target skill before reading its resources, preserving the host-provided authority and exact resource identifier. For example, a Poteto Mode link to `../pstack/CODEX.md` belongs to the Pstack router package, not the Poteto Mode package. Use the current catalog or the host’s documented explicit-selection mechanism; never invent an opaque package ID, reuse another session’s alias, or pass a sibling resource through the originating package. If the target cannot be selected, report the access limitation. A wrong-package read failure does not establish that the file is missing. Do not search private application stores, fetch another version, or run setup during ordinary work.

Distinguish packaged inventory, implicit discovery, explicit selection, and successful execution. This release packages 57 skills. `setup-pstack` and `automate-me` set `policy.allow_implicit_invocation: false` in `agents/openai.yaml`; the other 55 permit implicit invocation. A catalog filtered for implicit use can therefore return 55, while an installed-skill inventory may return all 57. Read invocation metadata, not only `SKILL.md` frontmatter, when auditing an omission. Complete supported pagination and distinguish policy filtering from context-budget truncation or unavailable access. Do not enable explicit-only skills merely to equalize counts.

## Delegate useful, bounded work

Pstack explicitly requests delegation for independent investigation, implementation slices with separate ownership, competing designs and independent review when it improves the task. A single coherent change does not require multiple agents. Use the smallest useful set of roles and schedule against the runtime's actual available slots. Never encode a universal worker count, depth, concurrency limit, model panel or cost claim.

The coordinator owns the complete playbook, acceptance criteria, integration and final answer. A worker owns a bounded responsibility. Give it:

- The goal, exact scope and current constraints, including later user corrections.
- The repository or artifact path and relevant revision when the work is revision-sensitive.
- Owned files or output paths, files it must not change and whether the task is read-only.
- Exact applicable guidance paths, especially this contract and the role brief.
- The relevant playbook section, evidence required, permitted checks and stop conditions.
- Whether nested delegation is useful and permitted within the assigned slice.

Workers read the relevant guidance themselves. Pass compact task context and file pointers; do not copy the entire repository, every skill or raw log into each prompt. A history fork does not establish that a worker has read a resource. A worker must not re-run the whole router, recruit another coordinator for the same job or expand its assignment into adjacent work.

Use a fresh worker for an independent task or an independent review. Continue with an existing worker when it owns relevant state, an active process, an unfinished edit or a coherent follow-up. Send a consolidated correction when scope changes. After interruption, verify current artifacts and explicitly restate what still applies before resuming. A stopped turn is not a completed task.

## Use the exposed agent lifecycle

Codex clients and releases expose different APIs. Select from the tools actually available in the session, read their schema and use one coherent lifecycle. The following names describe known tool families, not a promise that they are installed.

| Operation | Collaboration family, when exposed | Older native family, when exposed |
| --- | --- | --- |
| Start a bounded worker | `collaboration.spawn_agent`, with its supported `task_name`, `message` and fork fields | `spawn_agent`, using the actual prompt and role fields in its schema |
| Message a running worker | `send_message`; it does not start a turn | `send_input`, with interruption only when intended |
| Continue an idle worker | `followup_task`; it starts a turn | The available send/resume lifecycle; inspect status first |
| Await progress | `wait_agent` signals mailbox activity; read delivered messages and final notifications | The exposed `wait_agent` or `wait`, using its actual targets and timeout fields; inspect completion/status |
| Inspect or stop | `list_agents` and `interrupt_agent` | Exposed status, interrupt or `close_agent` tools |

A spawn acknowledgement is not a result. Wait for terminal output or a specific blocker, inspect the artifacts and integrate them. A mailbox wake is not the worker report. A timeout is not failure or completion. Batch independent waits when supported, avoid busy polling and continue useful parent work while children run.

Some hosts expose collaboration tools only as direct calls. Do not try to call them through a code-execution `tools` object unless that runtime explicitly exposes them there. Do not turn a missing native tool into a shell-launched agent process, an API loop, a guessed MCP call or a user-visible chat.

User-owned chats and native subagents are different. Use app chat-creation and cross-chat messaging tools only when the user requests those actions. Do not use `create_thread` to emulate worker spawning. Local shell process IDs, tool cell IDs, agent IDs and chat IDs are distinct identifiers; pass each only to its documented lifecycle tool.

On a runtime with a close/release tool, collect the report and release a finished worker when appropriate. If only interruption is exposed, use it to stop owned running work, not as an invented slot-release operation. Respect capacity errors and continue serially or wait for an existing worker. Never alter configuration to bypass the limit.

## Models and forks

This package's user-selected policy permits only `gpt-6.1-sol` and `gpt-6-astra`. Never select Luna, another model, reasoning below High, or Ultra. Permitted effort values are `high`, `xhigh` and `max`. The UI calls `xhigh` Extra High; pass the exact value accepted by the live tool rather than the display label.

| Selected model | Default effort for a new worker |
| --- | --- |
| `gpt-6.1-sol` | `xhigh` (Extra High) |
| `gpt-6-astra` | `high` (High) |

Prefer the user's currently selected permitted model. Use its default pair above unless the user explicitly selected another permitted effort for the task or workers. Max is allowed when requested, not an automatic escalation. When the parent selection is unknown, use `gpt-6.1-sol` with `xhigh` if the live schema exposes that pair. This package's policy authorizes these supported worker overrides; it does not authorize changing global configuration or switching the running parent.

Before each spawn, check the model, effort and fork combination against the live tool schema. Inherit settings only when the resolved child settings are known to comply with this policy and preserve the selected pair. Check applicable agent defaults when they can override inheritance. Do not assume an unspecified effort is safe: a model-only override may select the model's lower default. With explicit overrides, pass both model and effort.

Some full-history forks inherit settings and reject overrides. If the inherited pair is unknown or disallowed, use a supported fresh-context mode with an explicit permitted pair and a self-contained brief containing scoped instructions and evidence pointers. If neither compliant inheritance nor a compliant override is available, do not spawn. Continue directly where useful, report the delegation limitation and identify any required user model selection. Report a known parent-policy mismatch; a skill cannot retroactively change the model running the current turn.

Do not translate Cursor model names, append effort or speed suffixes, invent fallback slugs, set a paid service tier or require multiple providers. On rejection, report the actual limitation instead of cycling guessed values. Independent reviewers on the same model are independent perspectives, not model diversity.

Upstream `poteto-agent` and Comment Sicko are instruction roles. Their Codex versions live in [poteto-agent.md](references/agents/poteto-agent.md) and [comment-sicko.md](references/agents/comment-sicko.md). Pass the applicable role in the worker brief. Do not pass an invented `subagent_type` or assume an `agent_type` field exists.

Plugin `agents/openai.yaml` files describe skill UI and invocation policy. They do not register executable custom agents. Standalone `.codex/agents/*.toml` configurations are a separate host feature and require an explicitly requested setup change. This package does not install them.

## Shared files, permissions and evidence

Assume workers share the checkout and filesystem unless you have actually created and assigned isolation. Spawning or forking conversation context does not create a worktree. Separate concurrent writes by files or by real worktrees. Serialize changes to shared configuration, lockfiles, branch state and integration files. Do not switch branches in a checkout another worker is using.

When isolation is needed, inspect existing worktrees, preserve unrelated changes and use the supported worktree tool or local Git within scope. Record the actual returned path and baseline. Uncommitted work is not automatically copied to a new worktree. Review the candidate diff and integrate deliberately. Do not discard user changes or delete a worktree as an incidental cleanup step.

A read-only role brief is an instruction, not a sandbox. Subagents inherit applicable parent permission settings. Do not loosen approvals, sandboxing, network rules or authentication for a delegate. If a required approval cannot be presented, report the blocker and continue independent authorized work.

Read actual artifacts, not just worker summaries. Check revision-sensitive findings against the current head. Independent review has a separate verdict and must not silently edit the implementation under review. Fix supported findings and rerun only affected verification. Distinguish executed tests, static inspection, unavailable checks and installation acceptance. Follow repository/user restrictions on lint, type checking and other commands, including composite scripts.

## Other host capabilities

| Need | Codex behavior |
| --- | --- |
| Search, inspect or edit files | Use available file/command tools. Prefer narrow `rg` searches. |
| Plan multi-step work | Use a native plan tool if exposed, or a concise local plan. No invented `TodoWrite` API. |
| Clarify a material unknown | Use the host's user-input mechanism. Answer observable questions by inspecting or experimenting first. Keep approval separate. |
| Verify a CLI or running process | Use supported command/PTY tools and track owned process IDs. |
| Verify a UI | Discover available browser or computer-use tools and their instructions. Do not require Cursor control skills or disable security to obtain a browser. |
| Research OpenAI behavior | Prefer the official OpenAI Docs connector when available; otherwise use official OpenAI documentation. Runtime schemas govern actual calls. |
| Resume known work | Use supplied evidence or supported chat/history tools within authorized scope. Do not scan hidden transcript stores. |
| Continue long work | Keep a concise checkpoint and coordinate live work using native lifecycle tools. Respect user pause/cancel and actual budget limits. |
| Schedule future work | Only after the user asks for a reminder, monitor or recurrence, use the supported app automation tool and its returned schedule. A live wait is not durable automation. |

This port does not run upstream Cursor orchestration, PR-watch daemons, transcript scanners, hooks or model-setup scripts. Their engineering outcomes are implemented in native playbooks. A missing host capability is a specific limitation to report, not a reason to pretend an operation ran.

Official references: [subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents), [skills](https://learn.chatgpt.com/docs/build-skills), [plugin packages](https://developers.openai.com/plugins/build/plugins), [AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md). Source pins and audited implementation paths are recorded in the package's provenance and source audit.
