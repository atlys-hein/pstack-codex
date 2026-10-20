# Worktree and simulator cleanup

Read the [Codex execution contract](../../pstack/CODEX.md). An audit request is read-only. Removal requires explicit authorization for the resources concerned, even when a directory appears temporary.

1. Capture disk usage and inventory actual worktrees with `git worktree list --porcelain`. For Codex-managed worktrees, inspect the current chat's attachments and supported app inventory. Record path, branch, HEAD, tracked changes, untracked and relevant ignored files, merge state, upstream state, PR state, and measured size. Do not infer paths from an editor-specific directory convention.
2. Check active and pinned chats, running workers, terminals, dev servers, and other resource users through supported tools. A clean or merged worktree can still be active. Missing usage information is a hold reason. Do not scan unrelated transcript stores to manufacture certainty.
3. Present the candidate set and why each appears removable. Preserve unpushed commits, uncommitted edits, and useful untracked or ignored files. A directory called scratch is not proof that its contents are disposable. For an audit-only task, stop with the findings.
4. For authorized Codex-managed cleanup, prefer the app's worktree archive tool when available and read its guarantees and exclusions first. Its recoverable snapshot may exclude ignored files. Do not bypass pinned, primary, shared, or repository restrictions with shell deletion.
5. For an explicitly authorized ordinary Git worktree, use the supported non-forcing removal path after verifying it is unused and recoverable. If removal refuses because work remains, inspect and report it. Do not escalate to forced removal or recursive deletion without authorization covering that exact loss. Remove branch refs only if separately requested.
6. Treat simulators, SDK runtimes, build artifacts, and package caches as separate candidates. Inventory their actual size and usage first. Remove only the named authorized set through the owning tool. Do not run bulk delete-all commands or expand a worktree cleanup into unrelated application data cleanup.
7. Re-list the affected resources and measure disk usage again. Distinguish logical bytes removed from observed free-space change, which may be affected by snapshots and other processes.

Reply with what was audited, archived or removed, observed space reclaimed, and resources held back with concrete reasons.
