# Porting decisions

## Prepared 0.15.36 Codex update

Candidate `0.15.36-codex.1` adapts Poteto’s [Pstack 0.15.36 at c742dd61](https://github.com/cursor/plugins/tree/c742dd61706fbacc1b95f1a20b7b988cf096ce6c/pstack), checked on 2026-10-28, from the installed `0.15.29-codex.6` baseline. This candidate is prepared locally for user review. No commit, push or plugin publication is part of its validation. The installed private plugin remains at its observed release until the user authorizes publication.

The current inventory is 59 skills: all 58 upstream skill names plus the Codex router. There are 23 playbooks and 24 engineering principles. Only `setup-pstack` and `automate-me` remain explicit-only; 57 skills permit implicit invocation. These are package counts, not a fresh installed catalog test.

## Upstream coverage in this candidate

| Change | Codex adaptation |
| --- | --- |
| Statechart compiler and tests | Bundled real compiler, fixtures, CLI, bounded model checks and rendering reference. Local dependency paths replace mise auto-installation. Human console diagnostics carry the user-required prefix. |
| Ketchup Video | Subtitled video from authorized work evidence, task-local rendering, decoded-frame and hold checks, honest missing-tool fallback. |
| Formal verification | Generated TLA+ verification skills refer to Statechart by name instead of copying commands that can become stale. |
| Interrogate | Only failures demonstrated by a run survive. Parent reruns evidence at the same source revision. Review scope stays read-only outside assigned scratch space. Obsolete reviewer/rubric references are removed. |
| Arena | Explicit supported model selection, rejected-candidate handling and optional judge failure are retained. The user permits an independent GPT-family judge for this port, preferably the other allowed Sol/Astra model. This intentionally differs from upstream’s cross-family requirement. |
| Poteto Mode and playbooks | Goal restatement, steer/resume context, pre-measurement decision, evidence-based blockers, change-scaled verification and finished-unit checkpoints. Autopilot-stack stops before merge and stacks only dependencies. |
| Orchestrate | Native Codex agents and actual lifecycle/status tools, local checkpoints, one owner per branch/PR and independent verification. No Cursor Project store, orch CLI, cloud-VM defaults or invented subscriptions. |
| Script fixes | PR fork identity, deadline-clipped waits and matching inline-code delimiters are expressed in native playbooks. Cursor PR-watch and transcript scanners remain excluded and were not executed. |
| Reflect | Editable source or an authorized override is the target. Installed plugin caches are never edited. |
| Branding | The installed plugin’s `pstack-brand-v5.png` icon references are brought into the GitHub candidate. The v5 image and `logo.png` have identical SHA-256 hashes. Existing onboarding metadata is preserved in its normalized location. |

The [source lock](source-lock.json) records upstream hashes. The [comparison](upstream-comparison.json) maps every changed upstream path to its treatment. The MIT license and original attribution are unchanged.

## Codex capability research

The audit compared official documentation with this session’s live schemas for native collaboration, command sessions, worktrees, user-owned chats, automation, plugins and browser verification. It confirmed fresh-context explicit model/effort overrides, direct collaboration calls, shared filesystem ownership and distinct agent/chat/session identifiers. Managed worktrees need attachment reuse checks, asynchronous completion and returned-path handling. Recurring monitoring uses a supported current-chat heartbeat by default, reuses matching schedules and preserves notification policy. No global configuration changes are needed to obtain these capabilities.

Official references: [subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents), [skills](https://learn.chatgpt.com/docs/build-skills), [worktrees](https://learn.chatgpt.com/docs/environments/git-worktrees), [scheduling](https://learn.chatgpt.com/docs/automations), [browser](https://learn.chatgpt.com/docs/browser), [plugin format](https://developers.openai.com/plugins/build/plugins), and [skill metadata](https://developers.openai.com/plugins/deploy/submission-errors#skill-agent-metadata-errors). Live schemas govern tool calls and account availability. Sol/Astra and reasoning restrictions are retained user policy, not claims about every Codex model.

The Codex source commit in `source-lock.json` belongs to the historical source audit. It is not claimed as a new source checkout. This update’s current evidence is official documentation, live schemas and the bounded runtime exercises recorded below.

## Current validation

- The declared Statechart `npm test` suite passed: 368 tests, zero failures, skips or cancellations. Tests ran with task-local Node 24.10.0, fast-check 4.5.3, Java 11 and checksum-verified TLC 1.7.4. Renderer tests used pinned Pele/Mermaid/jsdom in task-local caches with install lifecycle scripts disabled.
- Real packaged launcher runs using installed Bun passed the Login model (9 states/18 transitions), exposed MediaPlayer’s one-step `LoudWhenStopped` bug, and exited with a missing-dependency diagnostic without output or installation when TLC was unavailable. Charts and reports byte-matched the upstream fixtures. A Pele SVG was generated and its classes inspected structurally.
- A Ketchup Video forward test produced an 18-second, 1280×720, 24 fps silent MP4. All 432 decoded frames were checked against source slides. Its 9- and 8-second holds met the 27- and 21-word budgets. Both slides were visually inspected at chat size and one tight label was corrected.
- An independent Interrogate forward test reproduced a failing pending-order calculation without fixing the source. The parent reran the failure and confirmed it. This is a single-adversary behavior exercise with parent verification, not exhaustive review coverage.
- An independent port review found no actionable issues in inspected upstream coverage, ownership, authorization, model policy, dependencies and branding. Sol `xhigh` and Astra `high` fresh-context spawn requests were accepted. Effective backend settings are not independently observable.
- All 59 skills passed Skill Creator validation. JSON/YAML, local links, resource maps, icons, manifest agreement, the 8 KB entrypoint budget, upstream skill coverage and preserved invocation policy passed package checks.
- Codex browser inventory and attachment-list reads succeeded. New worktrees, schedules, user-owned chat creation, PR writes, installed-plugin discovery and resource-only navigation were not exercised. They are not required to prepare this local update.

The POSIX launcher and process cleanup were tested on macOS. Windows behavior is untested.

Post-install discovery and resource-only navigation require a later authorized installation check. A locally valid archive does not prove automatic skill selection on every host.

## Historical 0.15.29 release evidence

The following records describe earlier releases and their actual dates. They are retained as history, not fresh validation of the prepared candidate.

### Baseline of the historical record

Version `0.15.29-codex.4` retains [Lauren Tan (Poteto)'s Pstack](https://github.com/cursor/plugins/tree/88d47514b82e7c44f00f2b2a72ff6dd12158038c/pstack) `0.15.29`. On 2026-10-21, upstream head `190d28736eff128ec94f502a22c7fe0c4b56cd37` has the same Pstack tree as the pinned source. This revision corrects discovery expectations and cloud resource navigation. The upstream comparison below records the earlier transition from `0.15.25-codex.2`.

The upstream subtree comparison found 3 added files, 23 changed files, 146 unchanged files, and no removed files. [The path comparison](upstream-comparison.json) and [source lock](source-lock.json) record exact revisions and hashes. These counts describe source coverage, not quality or performance.

### Upstream update coverage

| Upstream change | Treatment in this port |
| --- | --- |
| `create-formal-verification-skill` | Added a Codex skill for selecting a property and verifier, recording bounds and code mapping, demonstrating failure on a scratch copy, and creating a project-local verification skill. |
| `maintain-formal-verification-skill` | Added a Codex skill for checking history, updating stale verification, replaying counterexamples, distinguishing drift from bugs, and keeping sync records honest. Read-only audits do not modify verification. |
| Ketchup | Retained the complete pending-item list, context for each decision, per-item risk, and prohibition on cutting items to satisfy a word count. |
| Sharpen | Retained the four expert-framing questions and rewritten prompt. It does not execute the underlying task. The upstream commit title says “return only the rewrite,” while the shipped instructions explicitly say to give four answers first; this port follows the shipped instructions. |
| TypeScript guidance | Replaced the branded-type assertion example with a validating type guard and updated the rule. Retained the earlier correction that a plain numeric duration still needs finite/nonnegative validation. |
| Setup, help, and recipes | Added formal-verification routing and optional setup suggestions; updated Sharpen and Ketchup descriptions. Setup remains read-only unless changes are requested. |
| Normalized skill names | `make-bot-ui` and `poteto-mode` were already normalized in the Codex port. |
| Manifest version changes | Updated both manifests to `0.15.29-codex.1`, the description to 57 skills, and the public repository links. |
| README and guide updates | Incorporated the relevant workflow changes into the Codex README, help, recipes, and acceptance guide. Upstream Cursor setup and guide pages remain outside the active package. |
| New Claude Code adapter | Excluded from the Codex package. It maps Cursor tools, paths, model rules, and commands to Claude Code; this port uses its existing Codex execution contract. |

All 56 current upstream skill names are represented, plus the Codex router: 57 skills, 23 playbooks, and 24 principles. The original MIT license and artwork are preserved. [Attribution](../NOTICE.md) distinguishes original authorship from adaptation maintainership.

### Codex execution

The [shared execution contract](../skills/pstack/CODEX.md) now distinguishes invocation policy from package inventory and specifies owning-package resource reads. It owns tool discovery, native agent lifecycle, supported model/fork combinations, bounded ownership, authorization, and parent verification.

| Upstream platform mechanism | Codex treatment |
| --- | --- |
| Cursor `Task` or Claude Code `Agent` fields | Actual exposed native tool schemas and bounded worker briefs |
| Fixed provider/model panels | The retained Sol/Astra policy and supported explicit model/effort pairs |
| Background flags and assumed cloud isolation | Actual agent lifecycle and explicit workspace ownership |
| Custom Modes, `/loop`, and platform-specific transcript stores | Host skill discovery, active-session coordination, authorized history tools, and scheduling only when requested |
| Cursor orchestration CLI, watchers, hooks, or model setup | Excluded; relevant engineering outcomes are expressed in native playbooks |
| Upstream agent registrations | Role briefs under `skills/pstack/references/agents/`, not invented runtime agent types |

No MCP connection, hook, custom agent configuration, or background runner is declared. `skills/poteto-mode/scripts/`, upstream automations, and Cursor/Claude setup files remain excluded. The existing TSV log helper is unchanged.

### Model policy

Only `gpt-6.1-sol` and `gpt-6-astra` are permitted, with `high`, `xhigh`, or explicitly selected `max` reasoning. Defaults remain Sol Extra High and Astra High. Inheritance requires known compliant settings; otherwise the coordinator uses a supported explicit pair or reports that compliant delegation is unavailable. This policy does not alter the current parent model or global configuration.

The independent reviewer and Sharpen evaluator in this update were spawned with explicit `gpt-6.1-sol` / `xhigh` fresh-context arguments. The runtime accepted those arguments; effective backend settings were not independently observable.

### Verification evidence and limits

- The independent static review covered the new formal skills and changed workflow callers. It identified a malformed Ketchup link and an overly restrictive Sharpen rewrite instruction. Both were fixed and the reviewer returned PASS.
- A forward test invoked the updated Sharpen skill with a checkout-performance prompt. It returned the four framing answers and a rewritten prompt, preserved the payment-provider and receipt-layout constraints, and did not execute the checkout task.
- YAML/JSON parsing, local-link resolution, manifest agreement, source coverage, unchanged execution-contract checks, file hashes, and archive integrity are checked during packaging.
- The skill-creator Python validator could not run because its Python environment lacks PyYAML. Ruby Psych parses the skill frontmatter and metadata instead. No dependency installation, lint, or type-checking was performed.
- Formal verifier execution on a real application was not tested in this package update. These skills do not bundle a verifier or claim a proof without executing a project-specific check.
- The 2026-10-15 native-agent smoke test and source audit are historical evidence. A subsequent 2026-10-20 audit reviewed the public Codex implementation at `014489466a1739c2c563cdfe57880c2c7c8680e3`, official documentation, and this desktop session's live schemas. No confirmed runtime or local package-loading defect was found.
- Official [plugin metadata and packaging guidance](https://developers.openai.com/plugins/deploy/submission) was rechecked on 2026-10-20. Successful package validation, saved plugin contents, fresh-chat discovery, and runtime behavior are separate claims. The [acceptance guide](../skills/pstack/ACCEPTANCE.md) covers post-import checks.

### Instruction-loading hardening in codex.2

The public loader limits an automatically injected Agent Plugin skill body to 8,000 UTF-8 bytes. Five entrypoints exceeded that limit. Their detailed guidance now lives in linked references, while entrypoints retain the essential workflow, constraints, and reference-selection instructions. The same catalog requires complete reads, including continuation after tool-output truncation; supporting references still require those complete reads.

Source evidence: [host_prompt.rs](https://github.com/openai/codex/blob/014489466a1739c2c563cdfe57880c2c7c8680e3/codex-rs/ext/skills/src/host_prompt.rs#L79), [render.rs](https://github.com/openai/codex/blob/014489466a1739c2c563cdfe57880c2c7c8680e3/codex-rs/ext/skills/src/render.rs#L22), and [catalog_prompt.rs](https://github.com/openai/codex/blob/014489466a1739c2c563cdfe57880c2c7c8680e3/codex-rs/ext/skills/src/catalog_prompt.rs#L11).

A fresh desktop chat independently discovered the installed `0.15.29-codex.1` catalog, including the router, Poteto Mode, and both formal-verification skills. It successfully read Poteto Mode, the sibling execution contract, the bug-fix playbook, and the sibling testing principle through the host's filesystem mechanism. This establishes discovery and cross-skill access on that installed desktop release, not automatic selection for every task or post-publication acceptance of codex.2.

The separate runtime exercise used two workers with disjoint files, a mid-task constraint, a completed-worker follow-up, and parent verification: all seven order-service tests passed, with only the two assigned files changed. Shell process completion was also observed through the returned process-session identifier.

Subsequent codex.2 acceptance passed in a fresh desktop chat: 14 file reads matched the published package. A separate cloud Work chat exercised real resource-only catalog and read tools: ten reads across five owning skill packages completed without errors, filesystem proxies or invented resource locators. Cloud and executor catalogs exposed 55 Pstack skills, so this verifies the exercised cross-package paths, not discovery of all 57 skills on that host. No global configuration, permissions, attribution, models, or invocation policies were changed.

The repository is public source for an independent adaptation. Publishing it does not change the audience of an existing private plugin or submit a plugin to a public directory.

### Skill branding and compatibility audit in codex.3

All 57 skills now declare `icon_small` and `icon_large` in `agents/openai.yaml`, with a real skill-local copy of the original Poteto artwork. Plugin-level branding alone does not supply these skill UI fields. Local assets avoid traversal segments prohibited by the current [submission rules](https://developers.openai.com/plugins/deploy/submission-errors#skill-agent-metadata-errors), even though the public Codex plugin loader supports shared parent assets. No artwork or attribution was changed.

The audit was refreshed against public Codex commit `46d252f8bf8b09f4ef765bc72e40f02c229da3e6` and official documentation on 2026-10-20. The acceptance guide now derives its expected version from the uploaded manifest; Correct’s UI description reflects structural prevention. Saved metadata and asset validation are distinct from visually observing every client render the icons.

### Discovery and resource navigation in codex.4

The earlier acceptance guide incorrectly required all 57 packaged skills in host discovery. The package has 55 implicit-enabled skills and two explicit-only skills, `setup-pstack` and `automate-me`, declared in their `agents/openai.yaml`. A 55-entry implicit-use catalog is consistent with that policy. Installed inventories and explicit pickers may expose all 57; initial prompt truncation is a separate concern. The [official skills documentation](https://learn.chatgpt.com/docs/build-skills#optional-metadata) explains the invocation flag. The policy itself is unchanged.

The 2026-10-21 cloud audit reported both explicit-only skills readable through explicit selection. It also demonstrated that reading a sibling resource through the originating package fails, while selecting the owning package succeeds. This is evidence of a package boundary, not missing files. Earlier successful cross-package reads did not prove that the navigation instructions were sufficient. The contract now states the owner-selection procedure, and every non-router entrypoint supplies the short instruction before its first cross-skill contract link. No session-specific aliases or opaque package IDs are bundled.

Acceptance checks now separate inventory, filtered discovery, explicit selection, resource access, and execution. Setup, help, and the index use the same distinctions. Figure It Out’s stale reference to a moved principles section now links to the current reference. The source lock and package manifest record the current review rather than treating the old catalog count as an unconditional expectation.

Current-source inspection uses Codex `c7234c1174b27d9c55199fba0d546dc27d1b0415`. Structural checks and independent instruction review apply to this revision. Recorded cloud observations apply to the preceding installed release; they are not a fresh cloud execution of codex.4. No lint or type-checking is part of this documentation update. A deep audit cannot establish that every future host or workflow is defect-free.
