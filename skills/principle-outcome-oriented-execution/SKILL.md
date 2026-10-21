---
name: "principle-outcome-oriented-execution"
description: "Apply during planned rewrites and migrations with explicit phase boundaries. Converge on the target architecture; don't preserve smooth intermediate states with throwaway compatibility code."
---

On resource hosts, select the target skill’s owning package from the current catalog or supported explicit selector before reading a cross-skill link; retain its provided authority and resource identifier.

Read the [Codex execution contract](../pstack/CODEX.md). Apply this principle within the requested scope and permitted validation.


# Outcome-Oriented Execution

Optimize for the intended, verifiable end state rather than preserving smooth intermediate states.

**Why:** Keeping every intermediate step fully stable often creates temporary compatibility code that becomes long-lived debt. Converge on the target architecture and prove correctness at explicit verification boundaries.

**Core rule:**
- Prioritize end-state integrity over transitional stability
- Intermediate breakage is acceptable when it is planned, scoped, and reversible

**Guardrails:**
- Use this for planned rewrites and migrations with explicit phase boundaries
- Declare where temporary breakage is acceptable
- Keep high-signal checks for actively touched areas while migrating
- Run the relevant permitted checks at plan completion and explicitly report unavailable or prohibited checks
