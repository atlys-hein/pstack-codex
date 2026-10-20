# Pause safely

Read the [Codex execution contract](../../pstack/CODEX.md). Pause only on an explicit stop or pause request, or when an actual environment limit requires a handoff. "Going to bed, keep going" is not a pause request. Context compaction needs a checkpoint, not abandonment of the task.

1. Stop launching work. Finish the current safe atomic action and tell active workers to stop writes. Use supported interruption tools where needed, then inspect their state and outstanding processes before treating them as stopped.
2. Preserve existing edits and artifacts in place. Do not discard work, delete resources, publish a PR, push, or create a WIP commit merely to pause. If committing is already authorized and useful, follow the repository's convention and report the exact result.
3. Write a concise resume note in the permitted durable task area. Record intent, authorization, constraints, completed work, executed verification, current branch and worktrees, owned dirty files, worker and process state, known blockers, relevant paths, and the next action. Link an existing decision trail instead of duplicating it.
4. Record any external jobs or automation that may still run. Stop or modify them only within the user's request and the tool's capabilities. Do not claim every process stopped if it was not observed.

Reply with the checkpoint location, what remains on disk or running, verification state, and first resume action. Describe the work as paused, not complete.
