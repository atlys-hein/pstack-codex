# Refactoring

Read the [Codex execution contract](../../pstack/CODEX.md). The behavior contract stays fixed while the structure changes. Report unrelated features and bugs instead of expanding the refactor to absorb them.

1. Read the affected subsystem and callers with **how**. Pin the behavior through existing tests, a focused characterization test, a replay, or an equivalence harness. Use the smallest meaningful evidence for the requested change. Compilation alone is not a behavioral pin.
2. Name the structure that needs improvement and the target shape. Explain which branches, invalid states, or tracing burden it removes. Keep a clear local shape rather than adding an abstraction to satisfy a pattern.
3. Use **architect** when the target changes a significant boundary. For a large migration, route to **figure-it-out**. Keep deletions and cleanup within the refactor's scope.
4. Move in small behavior-preserving units and verify each one. When changing an internal API, migrate the affected callers and remove the obsolete path in the same coherent wave. Preserve public compatibility requirements explicitly. Search code, configuration, strings, prose, and back-references for renamed symbols.
5. Delegate independent mechanical slices when useful, giving exact names, paths, behavior pins, and exclusions. Shared primitives and callers with coupled edits belong to one owner or a sequenced phase. Do not let native workers race over shared files.
6. Prove equivalence on the real artifact. A baseline replay, observable output comparison, or matching-surface smoke run may be appropriate. Respect the permitted validation commands and report unsupported checks.
7. Review the complete diff for unrelated changes and added indirection. Keep the refactor only if it improves the requested structure while preserving the contract. Undo only owned changes if an experiment fails.
8. Shape commits and use [Opening a PR](opening-a-pr.md) only if authorized. Verification units do not require a history rewrite.

Reply with the structural change, pinned contract, equivalence evidence, maintainability effect, and any remaining limits.
