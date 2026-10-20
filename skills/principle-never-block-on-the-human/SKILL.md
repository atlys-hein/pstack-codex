---
name: "principle-never-block-on-the-human"
description: "Apply when tempted to ask 'should I do X?' on reversible work."
---

Read the [Codex execution contract](../pstack/CODEX.md). Apply this principle within the requested scope and permitted validation.


# Never Block on the Human

The human supervises asynchronously. Agents must stay unblocked. Make reasonable decisions, proceed, and let the human course-correct after the fact. Since code changes are reversible and reviewable, a wrong decision usually costs less than blocking.

- Proceed, then present. Do the work, show the result. Don't ask "should I do X?" Do X, explain why.
- Fix problems introduced by the authorized change. Report unrelated findings without expanding the task.
- Follow existing authorization for external writes and destructive actions. Complete reviewable preparation before asking for a missing decision.
- Requested reversible local work, such as editing code, keeping task notes and splitting work, proceeds without redundant confirmation.
- Product direction comes from the human. Execution should not block.
