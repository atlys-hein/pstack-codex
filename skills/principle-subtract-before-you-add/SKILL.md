---
name: "principle-subtract-before-you-add"
description: "Apply when sequencing an addition, refactor, or rewrite. Remove dead code, redundant validators, and stub references first, then build on the simpler base."
---

On resource hosts, select the target skill’s owning package from the current catalog or supported explicit selector before reading a cross-skill link; retain its provided authority and resource identifier.

Read the [Codex execution contract](../pstack/CODEX.md). Apply this principle within the requested scope and permitted validation.


# Subtract Before You Add

When evolving a system, remove complexity first, then build. Default to subtraction.

Simplify the code that must change for the requested outcome. Leave unrelated cleanup for a separate authorized task.

- Sequence removal before construction
- Cut before you polish (get to the minimum before investing in quality)
- Design for observed usage, not speculative edge cases
- No speculative validators, parsers, or guards beyond what the spec demands
- Simplify prompts (remove redundant instructions, excessive templates)
- When a reference has no novel content, delete it rather than leaving a stub
