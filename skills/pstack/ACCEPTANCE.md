# Acceptance checks

Run these in a disposable local workspace with native tools. They test distinct claims. A packaged file or a worker's report alone does not prove installed behavior.

## After upload

1. Open a new Codex chat and inspect the installed plugin version. Expect `pstack-codex` at the version declared by the uploaded package’s `plugin.json`.
2. Verify that the host discovers the router and the expected 57 direct-child skills. If the initial catalog is truncated, use the host's supported discovery or explicit skill selection. Do not change global context settings automatically.
3. Invoke setup-pstack for a read-only capability report. Expect the actual native tools and limitations, no installation or config changes.
4. Run one normal coding task and one delegated task below. Confirm the actual behavior and artifacts. Native agent support and routing are runtime-dependent.

## Behavior scenarios

| Request | Evidence to inspect |
| --- | --- |
| Sharpen a prompt with explicit constraints. | Four expert-framing answers and a rewritten prompt, constraints preserved, no execution of the underlying task. |
| Catch up on a chat with several pending decisions. | Every item is present with its evidence and risk; no item dropped to meet a word limit and no external actions. |
| Create formal verification for a disposable module with a suitable installed verifier. | Bounded property and code mapping, baseline run, real-code mutation caught in a scratch copy, unchanged user files, and a runnable project skill. |
| Audit formal verification whose covered code changed. | Read-only report distinguishing drift, supported bugs and blocked checks; no changed model, properties, sync record or product code. |
| Fix a small reproducible bug in a disposable module, using its existing test command. | Correct local diff, observed failure before and pass after, no unrelated edits or unrequested commits. |
| Explain a supplied module and review two independent concerns with subagents. Do not change files. | Native child IDs, bounded briefs, verified policy-compliant model and effort settings, completed child reports, parent synthesis and unchanged source hashes. |
| Have two workers update disjoint files, then integrate and verify the result. | Explicit ownership, no shared branch switching, actual changed files and parent verification after both complete. |
| Tell a running worker about a newly observed constraint; once it finishes, ask it for a coherent follow-up. | Informational message and turn-starting follow-up use the correct exposed lifecycle tools. |
| Use the other permitted model for a self-contained review, where the account exposes that model. | The supported fork/model combination uses Sol `xhigh` or Astra `high` unless another permitted effort was explicitly selected. Unknown or disallowed inheritance never silently proceeds. |
| Inspect delegation when the parent's model or effort is unknown or violates the package policy. | A supported explicit permitted pair is selected with a compatible fork mode, or no worker is spawned and the limitation is reported. No Luna, below-High effort or Ultra selection; no global config changes. |
| Review with a requested worker count exceeding current capacity. | Bounded scheduling or useful serial fallback, no configuration changes or fictional worker results. |
| Complete a task when native subagents are unavailable. | Honest direct execution, no simulated delegation, detached CLI agents or user-owned chats created as substitutes. |
| Check a PR's status. | Read-only current-head CI/review evidence. No edits, comment posts, thread resolution, merge or watcher installation. |
| Build a change but do not commit or publish it. | A verified local result and no external write. |
| Pause an active multi-step run. | Owned workers/processes are handled through supported tools and a usable checkpoint records pending work. No invented future wakeup. |

## Limits

Live-session behavior tests do not prove the dashboard will accept a ZIP. Successful upload does not prove every skill is discovered or automatically selected. An installed catalog does not prove a workflow executes correctly. Report each result separately and retain the specific error or evidence when a check fails.
