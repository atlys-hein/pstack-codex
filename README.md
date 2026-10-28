# Pstack for Codex

An independent Codex adaptation of **[Pstack](https://github.com/cursor/plugins/tree/main/pstack), created by [Lauren Tan (Poteto)](https://github.com/poteto)**. The engineering workflows, principles, playbooks, and original artwork come from her upstream project. The original [MIT license](LICENSE) and copyright notice are preserved. See [attribution](NOTICE.md).

This repository is maintained by [Heinrich Winterbach](https://github.com/atlys-hein) for the Codex adaptation. It is not an official release from Poteto, Cursor, or OpenAI.

## Version and upstream status

`0.15.36-codex.1` adapts Pstack `0.15.36` at commit [`c742dd61`](https://github.com/cursor/plugins/tree/c742dd61706fbacc1b95f1a20b7b988cf096ce6c/pstack), checked on **2026-10-28**. It contains **59 skills**, including the Codex router, **23 playbooks**, and **24 engineering principles**.

Changes from `0.15.29-codex.6`:

- Added Statechart's TLA+ compiler, diagrams, counterexample paths, upstream tests and rendering guidance. It requires explicit local TLC/Java dependencies and never installs global tools automatically.
- Added Ketchup Video for short subtitled catch-ups built from actual work artifacts.
- Interrogate now reports only reproduced failures, rerun by the parent, and separates blocked checks.
- Updated goal restatement, steer/resume context, pre-measurement decisions, change-scaled verification and dependency-aware PR stacking.
- Orchestrate uses native Codex agents and local checkpoints. Autopilot-stack performs the full workflow through verified, green PRs and stops before merging.
- Arena uses an independent GPT-family judge under the user-selected Codex policy, preferring the other permitted model when available. It reports this as independent review rather than cross-family diversity.
- Reflection targets editable source rather than plugin caches. Codex tool audits and source provenance were refreshed.

The [source lock](provenance/source-lock.json) pins the upstream source. [Porting notes](provenance/PORTING.md) explain which platform mechanisms were adapted or excluded. This is a port of the workflows, not a byte-for-byte mirror of Cursor or Claude Code integrations.

## Use in Codex

Import the plugin ZIP through your host's supported plugin installation flow, then open a fresh chat. Use the displayed skill names from the skill picker; a plugin namespace may be included. Of the 59 packaged skills, 57 permit implicit invocation. `setup-pstack` and `automate-me` remain available through explicit selection and may be omitted from implicit-use catalogs. On cloud resource readers, select the target skill’s owning package before following a cross-skill link.

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

## Runtime prerequisites

Statechart runs with Bun 1.1.5+, Node 22.18 to 22.x, Node 23.6+, or Deno 2.0+. It also needs Java and a TLC jar supplied through `TLA2TOOLS`, with optional `JAVA` for a selected Java executable. See the skill for the exact current command and supported bounds. SVG rendering uses Pele 1.9.0 when available. Ketchup Video needs an available video renderer and frame/probe tools. Missing dependencies are reported explicitly; the plugin does not install them or change global configuration. The POSIX launcher and process cleanup were exercised on macOS; Windows behavior is untested.

## Verification and limits

Structural validation covers skill metadata, manifest agreement, local links, package boundaries, source provenance, and file hashes. Behavioral checks and their limits are recorded in [porting notes](provenance/PORTING.md). Follow the [acceptance guide](skills/pstack/ACCEPTANCE.md) after importing an update; host discovery and available tools can vary.

Formal verification skills are instructions for building and maintaining project-specific checks. Bundling them does not prove a user's code correct or install a verifier.

The upstream Poteto artwork is included and referenced in both plugin manifests and in all 59 skills’ UI metadata. Each skill includes its own asset to support standalone and plugin loading. A prior ChatGPT listing displayed a generic icon despite those references; package inclusion does not guarantee that every listing surface renders it.
