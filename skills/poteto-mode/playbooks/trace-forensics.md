# Trace forensics

Read the [Codex execution contract](../../pstack/CODEX.md). The capture is a fixed dataset. Diagnose it without rerunning the workload or changing application code.

1. Identify the format, capture conditions, and available symbols. Use a suitable parser for CPU profiles or compressed traces, a text tool for a spindump, and the relevant heap tooling for snapshots. Delegate a large artifact to a read-only worker if its reduced output will save context.
2. Convert only as much as necessary into a queryable representation. For a large trace or heap, a table per sample, frame, or node can be useful. Preserve the original artifact and record transformation assumptions.
3. Narrow the mechanism. For CPU, inspect accumulated time and walk the call tree. For leaks, trace retained objects to GC roots. For hangs, inspect the blocked thread and wait reason. Distinguish sampling artifacts and missing intervals from actual absence of work.
4. Attribute frames through the artifact's own source mappings. Report file, symbol, and line when supported. A missing mapping is an explicit limitation, not a guessed source location.
5. Compare paired captures when available, accounting for differing durations and workloads. Without a confirming observation, label the finding as the strongest hypothesis the artifact supports.
6. Return a cited diagnosis. Do not implement a fix under this playbook. The throughput checkpoint is `not applicable, read-only forensics`.

Reply with the artifact format, reduced finding, source location, evidence paths, and what a paired capture did or did not confirm.
