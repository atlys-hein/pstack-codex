# Autopilot-stack

Read the [Codex execution contract](../../pstack/CODEX.md) and [Autopilot-full](autopilot-full.md). Reuse its ownership, evidence, and independent verification rules with the changes below. The deliverable is a reviewable linear dependency stack. The user owns landing unless they explicitly delegate it later.

1. Scope the queue and dependency graph. Each owner reports `STACK-READY` with exact head, intended parent, permitted checks, and evidence. No owner merges, closes a PR, enables auto-merge, retargets, or rebases independently. A dependent item starts from the observed parent tip in its own actual worktree; an independent item starts from the repository base.
2. Designate one topology owner. Only that owner performs authorized chain rebases, base retargets, and branch publication after coordinating with the branch owner. Shared files and branch refs still require exclusive ownership. Stop writers before changing their base and hand back the exact resulting head before they continue.
3. Append each verified item in dependency order. The root PR targets the repository's actual base branch. Each child PR targets its parent's branch. Use the available GitHub connector or supported CLI fallback. Read back the resulting base and head. Do not assume the default branch is named main or require a separate stacking service.
4. Absorb relevant base drift from the bottom up. For each link, compare its effective patch and parent context under [Shipping](shipping.md)'s validity rule. New heads get current checks and affected verification. A successful rebase is not itself proof that the chain still behaves correctly.
5. Put the verdict and its evidence where the user can review them, using local artifacts or authorized PR updates. Deliver the root and tip links, dependency order, current heads, and known gates. Do not publish review comments or resolve threads without authority covering those actions.
6. Once the user begins landing, freeze branch and topology writes. Only the designated, authorized transition of the next child to the actual merge result may proceed under Shipping. A newly discovered defect returns to the user or the established landing owner before any change races with a merge.

Choose Autopilot-full for independent PRs with landing authority. Choose this playbook for coupled changes, a requested stack, or a user-owned review and landing step.

Reply with the stack order, verified root and tip links, one verdict per link, pending checks or reviews, and excluded work with its reason. Do not describe STACK-READY as merged.
