# Autonomous run

Read the [Codex execution contract](../../pstack/CODEX.md). The parent owns a checkable exit condition and continues the authorized work until it is met or a concrete limit prevents progress.

1. State the predicate before the first iteration, such as the original repro passing, all named cases verified, or explicitly authorized PRs confirmed merged. Include user gates, budget, and environment constraints.
2. Work in verifiable units. Use native workers for independent scopes and native completion waits while other useful work proceeds. Poll external state only when it can affect the next decision, with bounded waits and backoff. Persistent scheduling requires an explicit user request and the supported app automation tool; absent that capability, record a resumable checkpoint instead of promising future execution.
3. Make the smallest change the evidence justifies, verify it, and preserve the accepted result. Discard only owned experiments that failed. Commit or publish only when already authorized.
4. Resolve in-scope blockers and routine choices from evidence. Report unrelated bugs, broken optional skills, or extra product work as follow-ups instead of creating an unbounded side project. A missing permission remains a gate even in an autonomous run.
5. Checkpoint through **show-me-your-work** after each meaningful unit. Record what changed, its evidence, the predicate's state, outstanding agents, and the next action.
6. Continue past a weak approach by revising the hypothesis. Stop on the met predicate, an explicit user stop, an exhausted budget, or a demonstrated blocker that requires missing access or a user decision. Do not silently relax success criteria or repeat failing calls indefinitely.

Answer a user's mid-run question and continue unless they cancel or change the task. A final report must distinguish a completed run from a checkpoint.

Reply with the exit condition, completed units, accepted and discarded work, final evidence, and any unmet condition.
