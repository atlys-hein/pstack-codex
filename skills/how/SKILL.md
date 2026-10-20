---
name: "how"
description: "Use for \"how does X work\", code walkthroughs before changing something, and placement / ownership / layering questions (\"where should this live\", \"which package owns this\", \"is this the right layer\"). Explains subsystem architecture, runtime flow, onboarding mental models. Use why for motivation."
---

Read [the Codex execution contract](../pstack/CODEX.md) before this workflow. It defines supported tools, bounded delegation, shared-checkout ownership, validation, and authorization. Use only capabilities exposed in this session.

# How

Explore the codebase to answer "how does X work?" questions. Produce architectural explanations at the level of a senior engineer onboarding onto a subsystem, enough to build a working mental model, not so much that it reads like annotated source code.

Use bounded, read-only delegation through the current native tools. Give each explorer an explicit question, source scope, expected citations, and no-write instructions. Apply the shared model policy before spawning. The parent owns synthesis and checks disputed claims against source.

## 1. Assess complexity

If the scope is ambiguous, state your interpretation and explore. The user can redirect.

- **Simple** (a single module, a small utility, a narrow question such as "how does function X work"): answer directly using `references/explainer-prompt.md` without its explorer-findings section. Go to step 4.
- **Complex** (a subsystem spanning multiple files or services, a cross-cutting feature, a full architectural overview): go to step 2.

When in doubt, take the simple path.

## 2. Explore (complex only)

Decompose the question into distinct source slices, usually two or three. Spawn bounded explorers with `references/explorer-prompt.md` and the assigned angle. If delegation is unavailable, inspect the slices sequentially and state that limitation.

## 3. Synthesize (complex only)

Once explorers return, synthesize using `references/explainer-prompt.md` and their cited findings. A separate explainer is optional when synthesis is substantial. Do not add another agent for a straightforward merge of results.

## 4. Present

Present the explainer's output. Light edits for clarity or context from the conversation are fine. Do not substantially rewrite it.

## Output format

The explanation uses the sections defined in `references/explainer-prompt.md`, dropping any that do not apply: Overview, Key Concepts, How It Works, Where Things Live, Gotchas.
