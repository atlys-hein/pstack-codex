---
name: "setup-pstack"
description: "Inspect Pstack capabilities and explain model, delegation, and validation settings in the current Codex environment. Change configuration only when requested."
---

On resource hosts, select the target skill’s owning package from the current catalog or supported explicit selector before reading a cross-skill link; retain its provided authority and resource identifier.

Read [the Codex execution contract](../pstack/CODEX.md) before this workflow. It defines supported tools, bounded delegation, shared-checkout ownership, validation, and authorization. Use only capabilities exposed in this session.

# Setup pstack

Report what this Codex session can actually do. This workflow is read-only by default.

## Inspect capabilities

1. Read the shared Codex contract and applicable project instructions. Locate installed Pstack through the current skill catalog or supported explicit selector, not a guessed cache path. When diagnosing discovery, compare the inventory with invocation metadata: 59 packaged skills, 57 permitting implicit invocation, and explicit-only `setup-pstack` and `automate-me`. Report the catalog type and any pagination or truncation; do not treat those two omissions from an implicit-use catalog as missing files.
2. Inspect the current tool catalog for native delegation, agent status and messages, repository access, browser or app control, connectors, and scheduling. Name unavailable capabilities explicitly.
3. Read relevant existing project configuration only when it changes the answer. Do not scan credentials, unrelated chats, or private application databases.
4. Determine available model overrides only from the live tool schema or runtime model catalog for this account. Use official documentation to interpret supported settings, not to infer availability. Do not infer model availability from a marketing name, alter a model identifier, or probe unsupported values by spawning agents.

## Report defaults

Pstack permits only GPT-6.1 Sol and GPT-6 Astra, with High, Extra High or Max reasoning. Its default pairs are Sol Extra High (`gpt-6.1-sol`, `xhigh`) and Astra High (`gpt-6-astra`, `high`). Report whether the resolved parent and child settings meet the shared model policy; do not report unknown inheritance as compliant. Luna, efforts below High and Ultra are excluded. The plugin cannot switch the current parent model or enforce runtime settings through manifest metadata. The orchestrator selects a workflow, gives children bounded tasks, assigns exclusive write ownership, drains their results, checks evidence, and synthesizes the answer. Workers use the active checkout unless an isolated worktree is explicitly assigned. Independent verification can use the same model family and must say so. Arena’s judge can use GPT models under the user-selected Codex policy. Prefer the other permitted model in a fresh context when available. Sol and Astra are both GPT, so this is independent review, not cross-family model diversity. If no permitted judge runs, the parent chooses with the rubric and reports the gap.

Explain capacity in terms of the host's actual agent limit. A small task can run directly. A substantial task usually benefits from a small number of independent workers. More workers increase cost and coordination work, so use them when independent scope or review value justifies it.

Report any existing app harness or `verify-*` skill. If none exists and the user's task needs product proof, point to **create-verification-skill**. Do not generate one during a setup-only request.

Also inspect whether the project has a skill that runs a model checker, prover, or other formal verifier against named code. If none exists, offer [create-formal-verification-skill](../create-formal-verification-skill/SKILL.md) once as an optional next step. If one exists, compare its sync commit with changes to the covered code and mention [maintain-formal-verification-skill](../maintain-formal-verification-skill/SKILL.md) when relevant. Generate or maintain verification only when requested; declining the offer does not block setup.

When asked about the new media and formal workflows, inspect Statechart’s prerequisites (Bun or a supported Node, Java and TLC) and Ketchup Video’s available render/probe tools. A missing renderer is a capability limit, not permission to install global tools. Report packaged executables separately from successful runtime checks.

## Optional configuration change

Change configuration only when the user asks for it. First inspect the supported configuration schema and existing file. Prepare a minimal edit that preserves unrelated settings. For a Codex CLI host that supports custom agents, use the documented project configuration and role files only when requested. For a desktop host, use its supported controls or tool parameters. A Pstack prompt file is not a registered agent type.

Do not install or reinstall plugins, change the user's default model, enable experimental features, or overwrite global configuration as a setup side effect. Do not write a private per-role model file that Codex does not load.

Return a compact capability table with available, unavailable, or unverified values; effective model behavior; any applied authorized change; and any concrete next step. Do not claim a capability passed a runtime test when only its schema was inspected.
