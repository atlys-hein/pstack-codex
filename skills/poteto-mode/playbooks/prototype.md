# Prototype

Read the [Codex execution contract](../../pstack/CODEX.md). A prototype resolves a decision cheaply. It is a throwaway artifact, not an implicit authorization for production implementation.

1. State the decision the prototype must settle: layout, interaction, density, behavior, timing, or approach. With no unresolved decision, use Feature for the requested implementation. A read-only investigation stays read-only unless a local experiment is within its scope.
2. Gather relevant prior art when the design space is open. Summarize the choices and infer a sensible direction from the request. Ask only when a missing preference materially determines the result.
3. Build in an allowed scratch directory separate from production source. Use the lightest available stack that exercises the question. Avoid production abstractions, installations, or new dependencies that the experiment does not need.
4. For meaningful alternatives, use one labeled switcher or a shared input case so differences are easy to compare. Use disjoint directories if native workers explore alternatives in parallel.
5. Observe the decisive behavior through the supported surface. Save screenshots for a visual choice and outputs or timings for a behavioral choice. Do not replace the observation with a self-reported opinion or a test that asserts the implementation.
6. Present alternatives, evidence, tradeoffs, and a recommendation. Preserve the useful artifact. Continue to Feature only when implementation is already requested; otherwise the decision and artifact complete this task.

Reply with the variants, evidence, recommendation, and scratch path. State plainly that the artifact is a prototype.
