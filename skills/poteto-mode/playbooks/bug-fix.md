# Bug fix

Read the [Codex execution contract](../../pstack/CODEX.md). The parent owns the diagnosis, scope, and final proof. Delegate a bounded investigation or implementation when useful, with one writer for each affected area.

1. Reproduce the reported behavior on the relevant surface using available browser, app, terminal, or test tools. Record the trigger, expected result, observed result, and environment. If the tool cannot reach the target, make the limitation specific and exhaust accessible evidence before requesting the missing observation.
2. Form competing causal hypotheses. Use **how** for the subsystem and **why** for regression history when relevant. Choose the observation that eliminates the most candidates. Confirm the surviving mechanism with runtime or test evidence before designing a fix. Add temporary instrumentation only when edits are authorized, and remove it when its evidence is captured.
3. Design the smallest root-cause fix. Use **architect** for a real interface or ownership decision. Give an implementation worker exact paths, the confirmed mechanism, the intended data shape, exclusions, and acceptance criteria. A worker owns its assigned slice and returns to the parent without routing another full playbook.
4. Verify the original trigger on the same surface. A unit test may protect a branch, but a wrong-surface or inconclusive result does not prove the reported bug is gone. Cover materially equivalent affected callers and variants.
5. Add a regression test when a meaningful, practical path exists. Demonstrate that it fails for the original defect and passes with the fix. Use **tdd** only when that cadence was requested. Do not create failing-test commits or rewrite history solely to stage the proof. Commit only with authorization.
6. Review the complete diff, remove disproven experiments, and run the smallest permitted checks. Follow [Opening a PR](opening-a-pr.md) only when requested or already authorized.

Every kept change must trace to the demonstrated mechanism or its regression protection. Preserve unrelated user edits when undoing an experiment.

Reply with the broken behavior, root cause, fix, failing and passing evidence, and any remaining verification limit.
