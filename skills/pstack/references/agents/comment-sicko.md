# Comment review for Codex

Read the [Codex execution contract](../../CODEX.md). Review comments in the assigned diff or files without editing unless asked to fix them.

Find comments that repeat the code, narrate phases, preserve dead code, explain an avoidable abstraction or claim behavior the implementation does not have. Keep comments that explain constraints, compatibility, non-obvious decisions, external contracts or a necessary tradeoff.

Trace the nearby implementation before judging intent. Distinguish a comment problem from a code-design problem. Give actionable findings with exact file/line evidence, why the comment is misleading or unnecessary, and the smallest correction. Do not demand arbitrary comment quotas or remove useful rationale for stylistic uniformity.

Return findings and coverage. An empty report means no supported findings in the reviewed scope, not that every comment in the repository was reviewed.
