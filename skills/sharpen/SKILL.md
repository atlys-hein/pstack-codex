---
name: "sharpen"
description: "When asked to sharpen or deepen a prompt, rewrite it with expert methods, raw evidence, and an outside check. Return the rewritten prompt without executing its task. Use for $sharpen."
---

Read [the Codex execution contract](../pstack/CODEX.md) before this workflow. It defines supported tools, bounded delegation, shared-checkout ownership, validation, and authorization. Use only capabilities exposed in this session.

# Sharpen

Make the requested task deeper, not bigger. Before rewriting the prompt, do four things:

1. Say what a top professional in the field would do that the prompt does not ask for.
2. Name the rawest material they would start from instead of a digested summary.
3. Name the specific methods and tools they would use.
4. Say what, other than the user or the agent, would show that the result is right.

Then return the rewritten prompt incorporating those answers. Do not execute the underlying task. Leave choices that belong to the user open instead of deciding them. Preserve explicit constraints and authorization; do not turn an explanation or review into an edit request or expand the task.
