# Autopilot-stack

Read the [Codex execution contract](../../pstack/CODEX.md) and [Autopilot-full](autopilot-full.md). Run Autopilot-full without merging. Build and verify the queue, then hand the PRs to the user to land. Independent PRs remain based on the repository base. Stack only actual dependencies.

1. Apply Autopilot-full's queue ownership, code-ready checks, independent verification, blocking rule, and authorized repair lifecycle. Stop before merge preparation and landing. An owner's brief can include readiness repair and babysitting under [Babysit](babysit.md); it does not authorize a merge or auto-merge.
2. Base a PR on another PR's branch only when it builds on that PR, following [Opening a PR](opening-a-pr.md). Each independent PR and each stack root targets the actual repository base. Read back every PR's actual base and head through the GitHub connector or supported fallback. Do not require a stacking service.
3. Each owner is the only writer of its branch, including its authorized rebases and retargets. A dependent PR rebases onto its parent's branch in place of the repository base. When a lower head changes, coordinate the affected owners bottom-up to restack and report their resulting heads. Preserve shared-resource ownership and observed remote leases.
4. A restack with an unchanged effective patch can retain evidence only under [Shipping](shipping.md)'s patch-and-context rule. Inspect the changed parent context as well as `git patch-id --stable`. Uncertain context or conflict resolution needs affected verification. Every current head still needs its applicable checks.
5. Stop when every PR is verified and green at its current head, with required approvals and user gates identified. Put each verdict and its evidence in permitted local artifacts or authorized PR updates. Handoff requires no merge, PR closure, or review-thread mutation. After handoff, nobody pushes or changes topology without the user's go. Any requested persistent follow-up must name this playbook and preserve the no-merge rule.

Choose Autopilot-full when landing is authorized. Choose this playbook when the user will land the PRs, whether the queue is independent or contains dependencies.

Reply with each PR's link, current head, base or parent, and verdict. Include dependency order, pending gates, parked follow-ups, and excluded work with its reason. Report the handoff as verified PRs for the user to land.
