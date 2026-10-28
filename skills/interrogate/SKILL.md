---
name: "interrogate"
description: "Use for \"interrogate\", \"adversarial review\", \"independent review\", \"challenge this\", \"stress test this code\", \"find blind spots\", or \"tear this apart\". Adversaries try to break a change or design; only findings proven by a run survive."
---

On resource hosts, select the target skill’s owning package from the current catalog or supported explicit selector before reading a cross-skill link; retain its provided authority and resource identifier.

Read [the Codex execution contract](../pstack/CODEX.md) before this workflow. It defines supported tools, bounded delegation, shared-checkout ownership, validation, and authorization. Use only capabilities exposed in this session.

# Interrogate

Adversaries try to break a change or a design. A finding survives only when a run proves it. A review request authorizes inspection and permitted scratch reproductions, not product fixes or external writes.

## Frame

Use the scope the user names. Otherwise inspect the branch diff from its merge base with the actual base branch, including relevant staged, unstaged and untracked changes. State the intent from the request, commits and PR description. Resolve observable uncertainty by inspection; ask only when missing intent materially affects the verdict.

## Fan out

Use [Arena](../arena/SKILL.md) Phase A’s runner selection and isolation rules, then Phase B’s native lifecycle. Two adversaries usually cover a substantial review; scale to the actual scope and capacity. Apply the shared model policy and disclose reduced independence if delegation is unavailable. Each reviewer sees the same scope and intent. Preserve the exact candidate revision and relevant uncommitted inputs in each owned scratch copy or worktree. Do not switch branches or alter the user’s checkout to reproduce a failure.

Give each adversary this brief:

> Break this change. Prove each finding with a run against the real code, such as a failing test, a repro script, or command output that shows the wrong behavior. For a design or plan, use a permitted scratch prototype or probe the current tree. Keep repros in your assigned scratch location. Report the title, exact command and working directory, inputs, actual output, expected output, and how the failure breaks the intent. Leave out unrun claims, style preferences, and risks that require a future change. No findings is valid. Do not fix the candidate or write external state.

A scratch path is not a permission boundary. Preserve repository restrictions on commands and side effects. If a necessary check requires unavailable access or additional authorization, report the blocked check separately; it is not a verified finding.

## Verify

The parent reruns each reported command against the same revision and inputs. Retain a finding only when the run reproduces a failure that breaks the intent. Merge findings with the same root cause. Skip Arena’s judge, base-picking and grafting phases: retain every verified failure rather than selecting one reviewer’s list. Never apply fixes as part of this review.

## Output

- **Intent:** the restatement and reviewed revision or source scope.
- **Findings:** each verified failure, command, actual and expected output, violated intent and reporting adversaries. Say “no verified findings” when none survive.
- **Dropped:** per adversary, the number discarded and reasons.
- **Blocked checks:** unavailable execution or evidence gaps, distinct from findings and passes.
