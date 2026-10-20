# Feature

Read the [Codex execution contract](../../pstack/CODEX.md). The parent owns the design, integration, and final verification. Delegate scoped implementation when it improves throughput or review separation.

1. Ground the requested behavior and existing contract with **how**. Name the user-visible result and the affected callers before choosing a structure.
2. Name the data shape, its owner, and the organizing structure. Use **architect** for meaningful new boundaries. Use **arena** only when competing implementations can resolve a material design uncertainty.
3. Record the throughput checkpoint. Keep each dimension, marking a genuine non-applicable case with a reason:
   - Blocking prerequisites that must finish before fan-out.
   - Independent workstreams and their owned paths.
   - Shared mutable state and how ownership prevents concurrent writes.
   - The smallest safe decomposition, including why one worker is sufficient when it is.
4. Assign each implementation slice a precise goal, file boundary, data shape, acceptance criteria, and permitted verification. A code-coupled feature has one integration owner; split only independent slices. Native workers may share the checkout, so do not assign overlapping files or let workers switch branches there. Competing implementations need actual isolated worktrees.
5. Review and integrate each returned slice. Re-ground upstream-derived files against their source. When changing a shared rule, identify and verify all affected consumers rather than patching one caller. Revisit the checkpoint when a phase changes ownership or contracts.
6. Prove the user-visible behavior on the relevant surface and run the permitted regression checks. Finish each verifiable unit before moving to a dependent one. An inconclusive result remains open.
7. Use an independent review for a high-risk change or a contested design. Resolve concrete findings and review the complete diff for scope and temporary artifacts.
8. Commit, push, and use [Opening a PR](opening-a-pr.md) only within existing authorization. Local edits alone do not authorize delivery actions.

Reply with what changed for the user, the material design choice, executed verification, and remaining decisions. Include the throughput checkpoint only when it helps explain the work.
