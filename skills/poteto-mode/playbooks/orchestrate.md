# Orchestrate

Read the [Codex execution contract](../../pstack/CODEX.md). Use this for a multi-unit program that needs sustained coordination, a dependency queue, and evidence carried between owners. Use [Autonomous run](autonomous-run.md) when one focused task and a few workers suffice. A program can be resumed across sessions, but native agents are not assumed to survive a restart.

## Roles and ownership

The parent is the coordinator. It frames the program, scopes briefs, consumes completions, integrates accepted work, and owns the human report. It assigns implementation and significant verification to bounded native workers when available. Keep the tree shallow. Add a sub-coordinator only when distinct tracks materially exceed the parent's coordination capacity, the runtime supports nesting, and its brief explicitly grants a scope and child budget. Do not infer nesting depth or capacity.

Each file, branch, database, port, and mutable resource has one writer. Native workers may share a checkout, so branches and worktrees must be explicitly allocated. Competing code requires actual isolation. One designated owner controls each stack's topology. A verifier receives a read-only assignment and a distinct evidence question. Independent verification does not require an unavailable model family.

Use fresh workers for independent units. Continue an owner for a fix round that relies on its current work or process. Before replacing it, stop its writes, reconcile its result, and transfer ownership. A delayed completion is checked against current state before it can be accepted.

## Durable program record

Use the repository's existing task area or the user-approved local scratch area. Do not assume a private agent store, install an orchestration runtime, or start a daemon. For a small program, one document or table is sufficient. For a larger program, separate these records only when their size or ownership requires it:

- Standing constraints, authorization, operator gates, and resource ownership.
- Units with id, dependency, owner, state, worktree or branch, current head, brief, and evidence.
- An ordered frontier with PRs, actual bases and heads, generation, and the lowest unmerged item.
- Verification rows keyed by unit or PR, head, base, scenario, verdict, and receipt path.
- A decision trail and unresolved gates.

The coordinator is the sole writer of the central record. Workers return scoped reports or write their own assigned artifact. Derive summary counts from the unit records instead of maintaining conflicting copies. Update existing rows without discarding unrelated evidence. Keep secrets and unrelated private chat content out of the record.

## Worker brief

Every assignment carries enough context to work without guessing:

```text
GOAL         The concrete outcome.
SCOPE        Owned paths, read-only paths, worktree or branch, shared resources.
CONTEXT      Current instructions, relevant source pointers, upstream evidence.
ACCEPTANCE   Observable criteria for accepting the unit.
VERIFY       Permitted commands or supported surface tools and pass predicates.
LIMITS       Time or effort budget, forbidden writes, unresolved authorization.
REPORT       Status, changed files, head/base if applicable, checks and evidence,
             findings, deviations, and remaining blockers.
DELEGATION   Whether nested delegation is allowed and its exact scope and budget.
```

Give dependent workers the actual upstream contract and accepted result, not just a unit id. Copy constraints into a minimal-context worker's brief or link a file it can actually read. A short mechanical unit can use one paragraph carrying the same essential facts. Sample briefs during a wave when quality is uncertain; repair the source brief before refilling a track whose workers repeatedly misunderstand it.

## Program procedure

1. Frame the countable done predicate, unit list, dependencies, budget, and user gates. Determine whether the requested outcome includes local changes, PRs, or landing. A plan-only request ends with the plan. Do not turn autonomous phrasing into unrequested delivery authority.
2. Inspect existing work and establish ownership. Record the current repository and forge state before assigning writers. Use a lightweight plan through supported tools or the local record. No plugin script is required to maintain the queue.
3. Pilot one representative unit through its permitted lifecycle. Confirm that the brief, unit size, and verification recipe work before scaling. A cheap repeated unit can serve as its own pilot; a novel or risky unit merits independent verification. The pilot ends at the authorized deliverable, which may be local evidence rather than a merge.
4. Start a rolling window of ready units within the actual runtime's concurrency limit. Refill as workers finish instead of waiting for an arbitrary batch's slowest item. Keep a useful local critical-path action for the coordinator. Do not occupy every slot with coordinators or sleeping watchers.
5. Process completions after a safe critical section. Record the result, inspect its evidence, classify it as accepted, needs verification, needs a scoped fix, blocked, or superseded, then recompute ready work. Review substantial diffs as a deliberate review task rather than losing the queue in an unbounded inline detour.
6. Integrate verified units continuously when their dependencies allow it. For a shared checkout, inspect the already-present diff instead of copying it again. For isolated worktrees, integrate only the reviewed owned result. Git commits, cherry-picks that change history, pushes, and merges follow existing authorization. Keep the lowest blocked dependency ahead of unrelated upper-stack repair.
7. At each meaningful checkpoint, reconcile every active child, current head, and evidence row. A completion notification is not proof of acceptance. A new head or base invalidates affected evidence until its validity is reviewed under [Shipping](shipping.md). Track unverified work explicitly.
8. Close by reconciling every unit and worker, validating the final artifact, confirming the done predicate, and preserving the record. Distinguish completed, intentionally excluded, blocked, and abandoned units. No unfinished work disappears into a summary.

## Stack safety

Use actual forge data to recompute dependency order after every authorized stack mutation. Never infer topology from branch names alone. One topology owner performs rebases, protected pushes, retargets, and merges. Other owners stop writes during the operation and receive the new base and head before continuing.

A PR owner controls its implementation slice. A babysitter follows [Babysit](babysit.md) at a recorded frontier generation and reports conflicts to the topology owner. A closed base or changed head requires re-reading the chain before further action. Do not close, retarget, or merge as incidental bookkeeping.

## Verification

Scale verification to actual risk. For a cheap, deterministic unit, a worker can run the prescribed check and the parent can inspect its receipt. Use a separate verifier for behavioral, ambiguous, or high-impact work. The ledger distinguishes `PASS`, `PASS+NOTES`, `FAIL`, and `BLOCKED`, and records the kind of proof, such as a live scenario, regression test, or document inspection. A static-only check does not prove runtime behavior.

Record exact head and base where code identity matters. The permitted checks are determined by the user and repository, not by this skill. Do not add mandatory lint, type-checking, or a fixed lane count. Unknown or blocked evidence remains unknown or blocked.

## Liveness and recovery

Inspect native agent state and observable outputs through supported tools. A follow-up starts work; do not use it merely as a status probe. Use bounded native waits and continue independent work. If the user explicitly requests persistent follow-ups, use the supported app automation tool with a clear predicate and meaningful-change notification rule. Otherwise checkpoint for manual or in-session continuation.

Classify a failure before retrying. A resource limit suggests smaller scope; a transient connection failure may justify one retry; a tool mismatch requires capability discovery rather than a guessed model or parameter. Repeated unchanged failure becomes a concrete blocker, not an infinite retry loop. Respect the user's budget.

A late worker result must reconcile with current ownership and code. Salvage unique evidence without blindly accepting old changes. When the shared acceptance criteria or infrastructure are broken, stop new assignments, safely drain or stop affected writers, fix the in-scope cause, then resume.

After a restart, read the durable record and current repository or forge state. Discover which jobs or native agents still exist through supported tools. Do not infer liveness from an old id or a transcript timestamp. Preserve existing changes and reconstruct only the remaining units.

## Escalation and reporting

Batch genuine user decisions and missing authorization in the record. Continue independent authorized work around those gates. Out-of-scope discoveries become follow-ups, not an expanding program. Stop immediately on a user hold, propagate it to every owner, and preserve a resumable checkpoint.

Report the predicate and measured count, accepted units and their evidence, current frontier, actual confirmed merges when authorized, unresolved gates, excluded or abandoned work, and the durable record path. During the run, report meaningful changes rather than repeating an unchanged table.
