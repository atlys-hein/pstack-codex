# Investigation

Read the [Codex execution contract](../../pstack/CODEX.md). The deliverable is a cited explanation, diagnosis, or recommendation. Do not edit code, external state, or configuration.

1. Use **how** to trace the relevant system. For motivation or history questions, also use **why**. Inspect the narrowest useful source first and expand when the evidence requires it.
2. Delegate independent source or history questions when their summaries reduce the parent's context load. Give workers read-only scope and require paths, observed facts, and uncertainty. Do not run an implementation router.
3. Build the answer from the inspected sources. For a mechanism, cover the overview, key concepts, flow, file locations, and relevant pitfalls. For a choice, compare the material tradeoffs and give a recommendation.
4. Distinguish observed facts from inferences. State the evidence that would resolve any remaining uncertainty. Apply **unslop** without deleting necessary technical detail.

The throughput checkpoint is simply `not applicable, read-only investigation`. There is no PR, monitoring loop, or mandatory design competition. If the user later asks for a change, route that work to the matching implementation playbook.

Reply with the cited answer and your judgment. Push back when the evidence contradicts the premise.
