# Acceptance checks

Run these in a disposable local workspace with native tools. They test distinct claims. A packaged file or a worker's report alone does not prove installed behavior.

## After upload

1. Open a new Codex chat and inspect the installed plugin version. Expect `pstack-codex` at the version declared by the uploaded package’s `plugin.json`.
2. Verify the package inventory contains 59 direct-child skills. Classify the host catalog before comparing counts: 57 skills permit implicit invocation; `setup-pstack` and `automate-me` are explicit-only in their `agents/openai.yaml`. Expect those two to be omitted from an implicit-use catalog, but not necessarily from an installed-skill inventory or explicit picker. Complete supported pagination and inspect truncation warnings. Verify both explicit-only skills through the host’s supported explicit selection, without changing their policy or global context settings. Record unavailable selection separately from missing files.
3. Invoke setup-pstack for a read-only capability report. Expect the actual native tools and limitations, no installation or config changes.
4. Run one normal coding task and one delegated task below. Confirm the actual behavior and artifacts. Native agent support and routing are runtime-dependent.

## Resource navigation

On a filesystem host, resolve links relative to the current file. On a resource-only host, select the target skill’s owning package using the current catalog or supported explicit selector, then read the exact linked resource with its provided authority. Do not carry the source skill’s package into a sibling read or construct opaque package IDs from an example.

Check Poteto Mode → Pstack’s `CODEX.md`, Pstack → `setup-pstack`, and a same-skill playbook read. Record explicit-only selection and cross-package access separately. If a wrong-package call fails, retain that evidence and retry through the verified owner; only a failure there supports an access problem. A successful recovery does not make the original navigation instructions friction-free.

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

## New workflow acceptance

- Interrogate: run an existing failing check in a disposable module, retain only reproduced failures, rerun them in the parent, and confirm original source hashes are unchanged. Record blocked commands separately.
- Arena: use a fresh GPT-family judge under the Sol/Astra-only policy, preferably the other permitted model. Report same-family independence accurately. If no permitted judge runs, skip it explicitly. Never substitute unknown inheritance or an unsupported model.
- Statechart: run the bundled upstream tests, then exercise the packaged launcher on passing and failing TLA+ models with explicit local dependency paths. Inspect its chart and report, bounded or unchecked properties, exit behavior and no-overwrite protection. Missing tools must produce diagnostics without global installation.
- Ketchup Video: render a real scratch MP4, inspect a frame from every slide at chat size, and measure subtitle holds from decoded frames. This does not prove a plugin catalog can discover the new skill.
- Publication gate: prepare the research, diff and package without committing, pushing or uploading when the user requests review first.

## Limits

Live-session behavior tests do not prove the dashboard will accept a ZIP. Successful upload does not prove every skill is discovered or automatically selected. An installed catalog does not prove a workflow executes correctly. Report each result separately and retain the specific error or evidence when a check fails.
