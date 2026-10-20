# Pstack for Codex

An independent Codex adaptation of **[Pstack](https://github.com/cursor/plugins/tree/main/pstack), created by [Lauren Tan (Poteto)](https://github.com/poteto)**. The engineering workflows, principles, playbooks, and original artwork come from her upstream project. The original [MIT license](LICENSE) and copyright notice are preserved. See [attribution](NOTICE.md).

This repository is maintained by [Heinrich Winterbach](https://github.com/atlys-hein) for the Codex adaptation. It is not an official release from Poteto, Cursor, or OpenAI.

## Version and upstream status

`0.15.29-codex.3` incorporates Pstack `0.15.29` at commit [`88d47514`](https://github.com/cursor/plugins/tree/88d47514b82e7c44f00f2b2a72ff6dd12158038c/pstack), checked on **2026-10-20**. It contains **57 skills**, including the Codex router, **23 playbooks**, and **24 engineering principles**.

Changes from `0.15.25-codex.2`:

- Added skills to create and maintain formal verification, including bounded claims, counterexamples, drift checks, and mutation checks.
- Updated Ketchup to list every pending decision with enough context to act, without dropping items to meet a word limit.
- Updated Sharpen to return a deeper rewritten prompt without executing the underlying task.
- Updated TypeScript branded-type examples to use a validating type guard.
- Updated setup, help, and examples for the new workflows.

The [source lock](provenance/source-lock.json) pins the upstream source. [Porting notes](provenance/PORTING.md) explain which platform mechanisms were adapted or excluded. This is a port of the workflows, not a byte-for-byte mirror of Cursor or Claude Code integrations.

## Use in Codex

Import the plugin ZIP through your host's supported plugin installation flow, then open a fresh chat. Use the displayed skill names from the skill picker; a plugin namespace may be included.

- **Setup pstack** reports available capabilities without changing global configuration.
- **Poteto mode** selects a workflow for substantial engineering work.
- **Poteto Help** helps choose a skill.
- The [skill index](skills/pstack/INDEX.md) lists all entrypoints.

To package a checked-out revision using Git:

```sh
git archive --format=zip --prefix=pstack-codex/ --output=../pstack-codex.zip HEAD
```

The repository includes a portable Agent Plugins manifest and a synchronized Codex compatibility manifest. Importing a package and making its source public are separate actions; the repository does not install or publish a plugin automatically.

## Codex behavior and model policy

The [execution contract](skills/pstack/CODEX.md) owns native delegation, tool discovery, task scope, file ownership, authorization, and parent verification. Role briefs are supporting instructions, not registered custom agent types.

This adaptation retains its selected model policy: **GPT-6.1 Sol** and **GPT-6 Astra** only. Default worker pairs are Sol Extra High (`xhigh`) and Astra High (`high`). High, Extra High, and explicitly selected Max are allowed. Luna, reasoning below High, and Ultra are excluded. Inheritance is allowed only when the resolved settings are known to comply.

These are workflow instructions. They do not change global settings, grant permissions, make unavailable models callable, or enforce runtime security. Codex supplies the tools, models, connectors, authentication, and agent capacity. The plugin installs no MCP servers, hooks, background daemons, or model configuration.

## Verification and limits

Structural validation covers skill metadata, manifest agreement, local links, package boundaries, source provenance, and file hashes. Behavioral checks and their limits are recorded in [porting notes](provenance/PORTING.md). Follow the [acceptance guide](skills/pstack/ACCEPTANCE.md) after importing an update; host discovery and available tools can vary.

Formal verification skills are instructions for building and maintaining project-specific checks. Bundling them does not prove a user's code correct or install a verifier.

The upstream Poteto artwork is included and referenced in both plugin manifests and in all 57 skills’ UI metadata. Each skill includes its own asset to support standalone and plugin loading. A prior ChatGPT listing displayed a generic icon despite those references; package inclusion does not guarantee that every listing surface renders it.
