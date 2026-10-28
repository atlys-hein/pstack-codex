# Orchestrate

Read the [Codex execution contract](../../pstack/CODEX.md). Coordinate a standing program by assigning each unit and checking what its owner produces. Use [Autonomous run](autonomous-run.md) when one focused task and a few workers suffice. A program can resume across sessions, but native agents are not assumed to survive a restart.

## Roles and ownership

The parent is the coordinator. It frames the program, scopes briefs, consumes completions, decides, and owns the human report. It does not author or edit program code. Owners handle fixes, conflicts, rebases, and integration. If native workers are unavailable, report that limitation and use Autonomous run for useful direct work within the authorized scope.

Give each PR one owner for its authorized lifecycle. Only that owner writes, pushes, rebases, or retargets its branch. A base PR's owner closes or retargets it only after the coordinator checks the dependent PRs. Each file, database, port, and mutable resource also has one writer. Native workers may share a checkout. Allocate actual worktrees when simultaneous branch operations or overlapping code require isolation.

Use fresh workers for independent units. Continue an owner when a fix round needs its existing work or running process. A context fork does not copy a checkout. Apply the shared model policy to every spawn. Each PR gets a verifier that is not its author. Independent verification does not require a different model family.

Keep the tree shallow. Add a sub-coordinator only when one area has enough independent work to exceed the parent's coordination capacity. Its brief must permit nesting and bound its scope and child budget. It returns a rollup with evidence paths. Sample its briefs during execution. Set concurrency from the live runtime rather than a fixed count or depth.

## Durable program record

Use the repository's existing task area or the permitted local scratch area. One document or table is usually sufficient. Record:

- Standing constraints, authorization, operator gates, and resource ownership.
- Units with id, dependency, owner, state, worktree or branch, current head, brief, and evidence.
- PR dependencies, actual bases and heads, and the lowest unmerged item.
- Verification rows keyed by unit or PR, head, base, scenario, verdict, and receipt path.
- A decision trail and unresolved gates.

The coordinator owns the central record. Workers return scoped reports or write their assigned artifacts. Keep one source for unit state and preserve unrelated evidence. Do not assume Cursor's Project tracker, a private agent store, or cloud VM storage exists. Do not install an orchestration runtime, launch shell agents, or start a daemon.

## Worker brief

Every assignment carries enough context to work without guessing:

```text
GOAL         The user's current goal and the problem this unit solves.
SCOPE        Owned paths, read-only paths, worktree or branch, shared resources.
CONTEXT      Current instructions, relevant source pointers, upstream evidence.
ACCEPTANCE   Observable criteria for accepting the unit.
VERIFY       Permitted commands or supported surface tools and pass predicates.
LIMITS       Time or effort budget, forbidden writes, unresolved authorization.
REPORT       Status, changed files, head/base if applicable, checks and evidence,
             findings, deviations, and remaining blockers.
DELEGATION   Whether nested delegation is allowed and its exact scope and budget.
```

Give dependent workers the accepted upstream result and the contract it establishes. Include the necessary evidence or a path that worker can actually read. Do not assume sibling history is visible. A short mechanical unit can use one paragraph carrying the same facts. Every steer or resume carries the current goal, corrections, and still-applicable constraints. Repair a faulty brief before sending more units through it.

## Program procedure

1. Frame the countable done predicate, unit list, dependencies, budget, and user gates. Determine whether the requested outcome includes local changes, PRs, or landing. A plan-only request ends with the plan. Do not turn autonomous phrasing into unrequested delivery authority.
2. Inspect existing work and establish ownership. Record current repository state and, for PR work, authoritative forge state through the GitHub connector or supported CLI fallback. Use local Git for working-tree operations. No plugin script is required to maintain the queue.
3. Pilot one representative unit through its permitted lifecycle. Confirm that the brief, unit size, and verification recipe work before scaling. A cheap repeated unit can serve as its own pilot; a novel or risky unit merits independent verification. The pilot ends at the authorized deliverable, which may be local evidence rather than a merge.
4. Start a rolling window of ready units within the actual runtime's concurrency limit. Refill as workers finish instead of waiting for an arbitrary batch's slowest item. Use the exposed native lifecycle under the section below. Keep the coordinator available for evidence review and decisions. Do not occupy every slot with coordinators or sleeping watchers.
5. Process completions after a safe critical section. Record the result, inspect its evidence, classify it as accepted, needs verification, needs a scoped fix, blocked, or superseded, then recompute ready work. Review substantial diffs as a deliberate review task rather than losing the queue in an unbounded inline detour.
6. Have owners integrate verified units when their dependencies allow it. For a shared checkout, inspect the already-present diff instead of copying it again. For isolated worktrees, the owner integrates only the reviewed result. Commits, pushes, PR updates, and merges follow existing authorization. Keep the lowest blocked dependency ahead of unrelated upper-stack repair.
7. At each meaningful checkpoint, reconcile every active child, current head, and evidence row. A completion notification is not proof of acceptance. A new head or base invalidates affected evidence until its validity is reviewed under [Shipping](shipping.md). Track unverified work explicitly.
8. Close by reconciling every unit and worker, validating the final artifact, confirming the done predicate, and preserving the record. Distinguish completed, intentionally excluded, blocked, and abandoned units. No unfinished work disappears into a summary.

## Use the live native lifecycle

Read the tools exposed in this session and use one supported lifecycle. In the collaboration family, `spawn_agent` starts a worker, `send_message` steers a running worker, `followup_task` starts a new turn on an idle owner, and `list_agents` inspects status. A status check does not require sending a prompt. Use `wait_agent` for mailbox activity, then read the delivered reports. A spawn acknowledgement or mailbox wake is not a result. Use the older native family only according to its live schema when that is the available API.

Choose a supported wait shorter than 60 seconds and cap it at any remaining deadline. Continue useful coordination between waits. If the schema cannot provide such a wait, use its nonblocking status path. Inspect observable output before deciding that a worker stalled. Do not invent PR event subscriptions, a `Task` API, background permanence, or a durable loop. Do not use user-owned chat creation to replace subagents.

Check authoritative PR state before reporting it. Read current head, base, checks, reviews, and merge state through the connector or supported fallback. Use these reads when they can affect the next decision. Do not build a shell polling loop or relay every status line between workers.

## Coordinate dependencies

Stack a PR only when it builds on another PR. Its owner rebases onto its parent branch, while a root owner uses the repository base. Coordinate bottom-up changes so owners never write one branch concurrently. After a lower head changes, have affected upper owners restack and report their resulting heads. Recompute dependencies from actual forge data after any authorized topology change.

A babysitter reports conflicts to the branch owner. A closed base or changed head requires rereading the chain before more work. Do not close, retarget, or merge as incidental bookkeeping.

## Verification

Read the actual diff or artifact and the verifier's evidence. CI is one input to the verdict. Behavioral work needs observable behavior, not just a type check. Use [Autopilot-full](autopilot-full.md#blocking-findings)'s evidence rule to distinguish blockers from follow-ups. Send work back when it drifts from scope. Fix only issues that block the program and record the rest.

Scale re-verification to the change. Broad new behavior, a redesign, or a large new diff needs broad coverage. A minor fix, conflict resolution, or necessary rebase needs the affected verification. A wording-only change needs document inspection and applicable checks, with no new behavioral verifier. Bind every verdict to the current head and base, carrying forward evidence only under [Shipping](shipping.md)'s patch-and-context rule. Unknown or blocked required proof remains open.

## Liveness and recovery

Judge progress by artifacts, checks, commits or PR activity when authorized, and the native lifecycle state. Status prose alone does not establish progress or a stall. Account for each worker as active, completed, replaced, or absorbed into another scope. Before replacing a writer, stop it, confirm that it cannot keep writing, reconcile its artifacts, and transfer ownership.

Retry by cause. Reduce scope after a context or memory limit. A dropped connection can justify the same brief again. A tool error requires capability discovery, and any model change must obey the shared policy. After two failed retries, mark the unit blocked or dropped and replan around it. Do not silently treat it as completed.

A late worker result must reconcile with current ownership and code. Salvage unique evidence without blindly accepting old changes. When the shared acceptance criteria or infrastructure are broken, stop new assignments, safely drain or stop affected writers, fix the in-scope cause, then resume.

After a restart, read the durable record and current repository or forge state. Restate the user's current goal and constraints. Discover which jobs or native agents still exist through supported tools. Do not infer liveness from an old id or a transcript timestamp. Preserve existing changes and reconstruct only remaining units. A persistent follow-up requires the user's scheduling request and a supported app automation tool.

## Escalation and reporting

Batch genuine user decisions and missing authorization in the record. Continue independent authorized work around those gates. Out-of-scope discoveries become follow-ups, not an expanding program. Stop immediately on a user hold, propagate it to every owner, and preserve a resumable checkpoint.

Open the report with the user's goal and what the program achieved against it. Include each PR's live state, head, verdict, and link; confirmed merges when authorized; parked follow-ups; dropped units and reasons; decisions waiting on the user; and the record path. During the run, report meaningful changes rather than repeating unchanged state.
