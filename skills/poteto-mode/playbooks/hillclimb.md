# Hillclimb

Read the [Codex execution contract](../../pstack/CODEX.md). The parent owns the metric and experiment integrity. Delegate bounded attempts, then accept them only from measured evidence.

One hypothesis, one change, one measurement, then keep or discard. Do not stack unmeasured changes or claim a win from source inspection.

1. Ground the architecture with **how** and reproduce the complaint with a realistic workload. Name dimensions that can move the result, such as data size, history, state, and concurrency. Fix the metric, improvement direction, target, regression gate, and stopping budget before the first attempt. Honor a user-specified minimum attempt count; do not invent an expensive minimum. A changed target requires an explicit explanation rather than silently declaring success.
2. Before measuring, read **principle-explain-the-number** and **benchmark-checklist**. Name the result that would change a decision and the noise floor. Establish a repeatable procedure and prove its sensitivity with contrasting realistic cases. Report errors, completed work, sample counts, and spread alongside the metric. Freeze the accepted workload, procedure, and environment, record a sampled baseline, and confirm the regression gate before changing code. Reuse an existing harness when possible.
3. Keep a decision trail in the permitted scratch area through **show-me-your-work**. One row per attempt records id, hypothesis, change, before, after, delta, checks, verdict, and explanation. Read prior rows before repeating an idea.
4. Tie each hypothesis to a mechanism. For performance, consider the ordering in [Perf issue](perf-issue.md). Do not borrow that playbook's one-fix stopping rule when this task explicitly calls for sustained improvement.
5. Give an attempt worker a tight file boundary, hypothesis, frozen measurement procedure, and acceptance rule. Independent hypotheses may run in actual isolated worktrees. Measurements sharing a machine, database, or external service must not interfere; serialize them or separate their resources.
6. Compare before and after with enough samples to clear noise and run the regression gate. Keep a change only if the metric improves beyond noise while behavior remains correct. Discard only the attempt's owned edits; preserve unrelated changes. If commits are authorized, give each accepted improvement a focused commit. Log rejected attempts too.
7. On a plateau, inspect the limiting factor again, try another mechanism, or evaluate a justified combination of near misses. Do not accumulate speculative tweaks or weaken correctness to move the metric. A simplicity improvement that preserves the result can be valuable, but label it accurately.
8. Stop when the target and any agreed minimum are met, the budget is exhausted, or evidence establishes a concrete blocker. Report an unmet target plainly. Continue independent useful work while waiting for native workers. Persistent unattended wakeups require the user's scheduling request and a supported automation tool.
9. Review the complete accepted diff and follow [Opening a PR](opening-a-pr.md) only when authorized.

Reply with metric and workload, baseline and final values, percent delta when meaningful, accepted and rejected attempt counts, each accepted mechanism, the trail path, and the best remaining hypothesis.
