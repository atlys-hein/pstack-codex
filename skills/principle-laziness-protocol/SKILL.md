---
name: "principle-laziness-protocol"
description: "Apply when refactoring, evaluating diff size, or tempted to add abstractions, layers, or signal threading. Bias toward deletion and the smallest change that solves the problem."
---

On resource hosts, select the target skill’s owning package from the current catalog or supported explicit selector before reading a cross-skill link; retain its provided authority and resource identifier.

Read the [Codex execution contract](../pstack/CODEX.md). Apply this principle within the requested scope and permitted validation.


# Laziness Protocol

- **Consolidate decisions.** Do not repeat the same choice in several places. Put it behind one source of truth and pass the result as a simple flag.
- **Minimize the diff.** Make the smallest change that solves the problem. Fewer lines beat "elegant" boilerplate.
