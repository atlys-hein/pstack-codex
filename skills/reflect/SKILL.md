---
name: "reflect"
description: "Review the active conversation for durable lessons and propose focused edits to existing skills. Apply only edits the user requested or approves."
---

Read [the Codex execution contract](../pstack/CODEX.md) before this workflow. It defines supported tools, bounded delegation, shared-checkout ownership, validation, and authorization. Use only capabilities exposed in this session.

# Reflect

Mine the current conversation for durable lessons and route them to the existing skill that owns the behavior. Skip trivial sessions and issues already covered by guidance that was simply not followed.

## 1. Prepare the evidence

Use the active conversation context, native history tools, or an explicitly supplied transcript. If complete tool output is unavailable, provide an accurate digest with evidence gaps. Do not scan private application transcript stores or unrelated projects.

## 2. Review independently

For a substantial session, delegate the judgment, tooling, and divergent lenses using the templates in `references/`. Use native delegation, the shared model policy, explicit read-only scope, and the actual concurrency limit. Do not assume a special mode is required to access connectors. Small sessions can use one reviewer plus parent synthesis. If delegation is unavailable, apply the lenses directly and state that limitation.

| Lens | Prompt template |
|---|---|
| Judgment | `references/judgment-reviewer.md` |
| Tooling | `references/tooling-reviewer.md` |
| Divergent | `references/divergent-reviewer.md` |

Fill the template's context input with the scoped history or digest. Reviewers may read the referenced source records through available connectors, but may not edit files, create issues, or send messages.

## 3. Synthesize

Use `references/synthesizer.md` to produce Accepted, Rejected, and Backlog findings. The parent owns the final judgment. Delegate synthesis only when the evidence volume makes a separate pass useful. Spot-check citations and read each proposed target skill before accepting a change.

Move an item to Backlog if an existing structural mechanism would enforce it more reliably than prose. Scope all proposed enforcement to the demonstrated pattern.

## 4. Prepare and apply the authorized edits

A request to reflect alone produces reviewable proposed edits and their reasons. If the user also requested the skill updates, that authorization is enough for the in-scope local changes. Otherwise present concrete edits and ask before applying them. Do not create backlog tickets, PRs, or messages without separate authorization.

For substantive skill work, use the available Codex **skill-creator** guidance. Prefer a focused change to an existing skill. Tune its description when discovery failed, and create a new skill only when no existing owner fits and the pattern is durable. Preserve supported invocation metadata.

Validate touched skills with the available validator and inspect references. Return applied or proposed paths, what changed, deferred items, and rejected findings with reasons. Distinguish local recommendations from tickets actually created.
