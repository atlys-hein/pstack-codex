---
name: "no-comments"
description: "Review comments with an independent Comment Sicko role and remove confirmed redundant comments within the requested scope. Preserve documented constraints and protected comments."
---

On resource hosts, select the target skill’s owning package from the current catalog or supported explicit selector before reading a cross-skill link; retain its provided authority and resource identifier.

Read [the Codex execution contract](../pstack/CODEX.md) before this workflow. It defines supported tools, bounded delegation, shared-checkout ownership, validation, and authorization. Use only capabilities exposed in this session.

# No comments

Use an independent reviewer to find comments the code can express more clearly. This workflow does not authorize broad cleanup beyond the selected files or diff.

## Scope

Use the user's files or diff. Otherwise inspect the current working-tree and branch changes against the verified base. Preserve unrelated edits.

## Review

Read [Comment Sicko](../pstack/references/agents/comment-sicko.md), then pass that role brief, the scope, and read-only instructions to a native subagent. A role prompt is text, not a registered agent type. Apply the shared model policy before spawning. If delegation is unavailable, perform the review directly and disclose the missing independent pass.

Ask for each comment's location, evidence, proposed action, and any constraint it records. Inspect the referenced code and reject scope escapes, application-code changes by the reviewer, unsupported suppression removals, or findings that lack evidence. Use **how** or **why** for ambiguous `IMPORTANT` or `do not remove` comments. Ambiguity alone does not justify deletion.

## Act within authorization

For a review-only request, return findings without edits. For a request to remove comments or fix accepted findings, make the smallest proven local change. Keep licenses, required API docs, tool directives, externally imposed constraints, and suppression comments whose removal would hide or break a required contract.

A comment revealing a real workaround may call for a root-cause fix. Apply it only if that behavior change is already within scope. If the fix needs a different design, use **architect** to prepare the shape and stop at a sketch unless implementation is authorized. Do not delete a needed constraint merely because the enforcement change is unapproved or out of scope.

Where a constraint can be encoded cheaply in existing types, tests, or validation, present the concrete option. Honor repository restrictions on new tooling, lint, and type-checking. A skill does not expand those permissions.

## Verify and report

Inspect the full diff, verify accepted changes with the smallest allowed check, and report deletions, protected comments, behavior changes if any, validation, and unresolved constraints. Commit or open a PR only if requested.
