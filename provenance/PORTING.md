# Porting decisions

## Current baseline

Version `0.15.29-codex.1` ports [Lauren Tan (Poteto)'s Pstack](https://github.com/cursor/plugins/tree/88d47514b82e7c44f00f2b2a72ff6dd12158038c/pstack) `0.15.29` at `88d47514b82e7c44f00f2b2a72ff6dd12158038c`, checked on 2026-10-20. The previous port was `0.15.25-codex.2`, pinned to `f713f14203cd6420cec13cd7c55c32d598dbab68`.

The upstream subtree comparison found 3 added files, 23 changed files, 146 unchanged files, and no removed files. [The path comparison](upstream-comparison.json) and [source lock](source-lock.json) record exact revisions and hashes. These counts describe source coverage, not quality or performance.

## Update coverage

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

## Codex execution

The [shared execution contract](../skills/pstack/CODEX.md) remains unchanged in this update. It owns tool discovery, native agent lifecycle, supported model/fork combinations, bounded ownership, authorization, and parent verification.

| Upstream platform mechanism | Codex treatment |
| --- | --- |
| Cursor `Task` or Claude Code `Agent` fields | Actual exposed native tool schemas and bounded worker briefs |
| Fixed provider/model panels | The retained Sol/Astra policy and supported explicit model/effort pairs |
| Background flags and assumed cloud isolation | Actual agent lifecycle and explicit workspace ownership |
| Custom Modes, `/loop`, and platform-specific transcript stores | Host skill discovery, active-session coordination, authorized history tools, and scheduling only when requested |
| Cursor orchestration CLI, watchers, hooks, or model setup | Excluded; relevant engineering outcomes are expressed in native playbooks |
| Upstream agent registrations | Role briefs under `skills/pstack/references/agents/`, not invented runtime agent types |

No MCP connection, hook, custom agent configuration, or background runner is declared. `skills/poteto-mode/scripts/`, upstream automations, and Cursor/Claude setup files remain excluded. The existing TSV log helper is unchanged.

## Model policy

Only `gpt-6.1-sol` and `gpt-6-astra` are permitted, with `high`, `xhigh`, or explicitly selected `max` reasoning. Defaults remain Sol Extra High and Astra High. Inheritance requires known compliant settings; otherwise the coordinator uses a supported explicit pair or reports that compliant delegation is unavailable. This policy does not alter the current parent model or global configuration.

The independent reviewer and Sharpen evaluator in this update were spawned with explicit `gpt-6.1-sol` / `xhigh` fresh-context arguments. The runtime accepted those arguments; effective backend settings were not independently observable.

## Verification evidence and limits

- The independent static review covered the new formal skills and changed workflow callers. It identified a malformed Ketchup link and an overly restrictive Sharpen rewrite instruction. Both were fixed and the reviewer returned PASS.
- A forward test invoked the updated Sharpen skill with a checkout-performance prompt. It returned the four framing answers and a rewritten prompt, preserved the payment-provider and receipt-layout constraints, and did not execute the checkout task.
- YAML/JSON parsing, local-link resolution, manifest agreement, source coverage, unchanged execution-contract checks, file hashes, and archive integrity are checked during packaging.
- The skill-creator Python validator could not run because its Python environment lacks PyYAML. Ruby Psych parses the skill frontmatter and metadata instead. No dependency installation, lint, or type-checking was performed.
- Formal verifier execution on a real application was not tested in this package update. These skills do not bundle a verifier or claim a proof without executing a project-specific check.
- The 2026-10-15 native-agent smoke test and Codex source audit are historical evidence, not a new audit of today's Codex implementation. The source audit remains pinned to `bb64b894fd67158be0f874872e6d7bfe717e7368` in the source lock.
- Official [plugin metadata and packaging guidance](https://developers.openai.com/plugins/deploy/submission) was rechecked on 2026-10-20. Successful package validation, saved plugin contents, fresh-chat discovery, and runtime behavior are separate claims. The [acceptance guide](../skills/pstack/ACCEPTANCE.md) covers post-import checks.

The repository is public source for an independent adaptation. Publishing it does not change the audience of an existing private plugin or submit a plugin to a public directory.
