# Visual parity

Read the [Codex execution contract](../../pstack/CODEX.md). The agreed baseline is the specification. Verify equivalence with an image comparison as well as the relevant interaction checks.

1. Capture the baseline before migration across the required component states, viewport sizes, themes, and fonts. When matching two implementations, capture both under the same conditions. Without a baseline, do not claim parity.
2. Freeze the comparison conditions and pass threshold. Pixel-exact requests require zero meaningful pixel delta. Stabilize animation, time-dependent content, rendering environment, and random data before measuring. Do not loosen the threshold, edit the baseline, or restructure the component merely to conceal a mismatch.
3. Migrate shared primitives first, then independent components. Delegate disjoint components in isolated worktrees when needed; native workers do not receive isolation automatically. Give each owner the exact baseline and states it must preserve.
4. Run each component through the supported browser or app tools and compare images. Investigate every unexpected delta and verify the interaction contract. Iterate within the active session until the agreed predicate passes or a concrete blocker is demonstrated.
5. Review the complete result. Use [Opening a PR](opening-a-pr.md) only when the user requested that delivery. A component batch is appropriate when its dependencies and proof remain reviewable.

Reply with the components, measured diff result for each, baseline and evidence paths, and anything still unresolved.
