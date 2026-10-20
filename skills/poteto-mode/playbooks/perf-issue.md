# Perf issue

Read the [Codex execution contract](../../pstack/CODEX.md). The parent owns the measurement and the claim. Tie the fix to a reproducible workload rather than an intuition from source.

1. Capture a baseline on the actual relevant surface. Record workload, environment, work completed, errors, and the metric. Read **benchmark-checklist** before trusting the number.
2. Use **how** to connect the trace to the architecture. Consider these mechanisms in order, stopping when a supported change meets the target:
   1. Stop work whose result is unused.
   2. Reuse a result instead of repeating the work.
   3. Reduce how often the work runs.
   4. Defer work off the critical path.
   5. Schedule work outside the user's wait.
   6. Run independent work concurrently.
   7. Reduce the cost of the remaining work.
3. Plan the change from the measured mechanism. Use **architect** for a material interface decision. Delegate a bounded implementation if useful and review its diff. Verify each attempt before beginning another.
4. Capture the post-change artifact with the same workload and conditions. Parse traces or profiles into a queryable form when that makes the comparison reliable. Repeat enough samples to distinguish the delta from noise. Check that less work or more errors did not manufacture the improvement.
5. Run the relevant behavior regression gate. Discard only the task's own unsupported experiment after preserving concurrent work. Wrong-surface, missing baseline, or inconclusive measurements cannot support a speedup claim.
6. Report the evidence. Include it in a PR only when PR creation is authorized, using [Opening a PR](opening-a-pr.md).

For repeated optimization against one metric, use [Hillclimb](hillclimb.md).

Reply with baseline, result, units, delta, workload, artifact paths, and remaining uncertainty.
