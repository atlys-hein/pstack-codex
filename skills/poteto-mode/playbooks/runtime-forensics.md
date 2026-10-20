# Runtime forensics

Read the [Codex execution contract](../../pstack/CODEX.md). Diagnose the live symptom without shipping a fix or modifying source under a read-only request.

1. Identify the affected process and the accessible inspection tools. Capture the relevant signal through a supported, permitted mechanism: a CPU profile for a spin, a heap snapshot for a leak, or a trace for a rendering glitch. Record the trigger and environment.
2. Reduce the artifact to the load-bearing evidence: the hot function, retainer chain to a GC root, or recurring work without input. Delegate bulky artifact parsing to a read-only worker when useful. Return focused findings and exact artifact references.
3. Test the mechanism with further observations. Prefer existing instrumentation and supported read-only diagnostics. Injected code, runtime hotfixes, debugger side effects, or persistent instrumentation require authorization when they change the target's state; do not smuggle them into a diagnosis request.
4. Map the finding to source, including the symbol and the line that allocates, schedules, or blocks. If symbols or process access are unavailable, state the exact limit and the strongest supported hypothesis.
5. Compare a controlled trigger or paired capture when available. A correlation alone remains a hypothesis. The throughput checkpoint is `not applicable, read-only forensics`.

Reply with the captured signal, reduced finding, evidence for the mechanism, source location, artifact paths, and certainty. Continue to Bug fix or Perf issue only when a fix is requested.
