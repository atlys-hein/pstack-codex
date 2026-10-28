---
name: "arena"
description: "Spawn N parallel candidates at the same task, pick a base, graft the strongest parts of the losers into it. Use for $arena, 'arena this', 'throw it in the arena', or when one attempt at a non-trivial artifact would lock in the wrong shape."
---

On resource hosts, select the target skill’s owning package from the current catalog or supported explicit selector before reading a cross-skill link; retain its provided authority and resource identifier.

Read [the Codex execution contract](../pstack/CODEX.md) before this workflow. It defines supported tools, bounded delegation, shared-checkout ownership, validation, and authorization. Use only capabilities exposed in this session.

# Arena

Open a todolist with one entry per phase (Frame, Fan out, Cross-judge, Pick, Graft, Verify) before launching anything.

## Phase A: Frame

Every candidate gets the same prompt, so the prompt is the contract.

1. State the artifact each candidate is producing.
2. Derive the rubric, 3-6 concrete gradeable criteria for what success looks like on *this* task. It is the picker's tool in Phase D. Candidates only see the task.
3. Use two independent candidates by default when distinct alternatives can change the decision. Honor an explicit user count and cap active workers at the host limit. Apply the shared model policy, including its default effort pairs and verified inheritance rules. A different model is optional, never a condition of validity. On a rejected model selection, use only a supported pair permitted by the contract, or drop that candidate and explain why. Replace a dropped candidate when another permitted selection is available; never guess model identifiers or silently inherit unknown settings. If delegation is unavailable, generate alternatives sequentially and label the independence gap.
4. Give each candidate its own output location (an explicitly assigned worktree for conflicting repository edits, otherwise `work/arena-<slug>/candidate-<n>/`), per the **separate-before-serializing-shared-state** principle skill.

## Phase B: Fan out

Spawn candidates using the native delegation tool and its live schema. Give each the task, shared grounding, exclusive output path, allowed side effects, verification, and a request for a short rationale naming rejected alternatives. Candidates produce one artifact and must not recursively run arena. Launch independent work within the host limit and drain every result before synthesis.

If a candidate produces no output, proceed with N-1 and note the dropout.

## Phase C: Cross-judge

After all candidates stop writing, delegate one read-only judge in a fresh context when capacity and task value justify it. The user permits GPT-family judges in this Codex port. Prefer the other supported model within the shared Sol/Astra policy when it is available, using its permitted model/effort pair. If only one permitted model is available, use a fresh independent judge on that model and say so. Never guess a model, use unknown inheritance, or expand the allowed model set. Sol and Astra are both GPT models: call this independent review, not cross-family model diversity.

The judge sees the rubric and path-labeled candidates, scores each criterion, and recommends a base. Read the candidates yourself while it works. If no permitted judge can run, apply the rubric yourself in Phase D and report the skipped independent check.

## Phase D: Pick a base

Read every candidate end to end before picking. Score each against the rubric criterion by criterion, not on holistic feel, and compare with the cross-judge when Phase C ran one. Agreement on the base confirms the pick. Disagreement means one of you is biased or the rubric was ambiguous. Read both rationales before deciding.

Pick the base a future maintainer can extend most easily without breaking invariants. When two feel tied, prefer the cleaner boundary or smaller API, per the Laziness Protocol.

## Phase E: Graft

Walk each losing candidate once more for what is worth porting into the base, usually one or two things per candidate, not most of it. Fold each graft in by hand, per the **redesign-from-first-principles** principle skill, so the result stays coherent under one mental model. Don't paste mechanically.

If the candidates converge on one shape, that is strong agreement. Note it and ship the consensus shape. No graft is needed. If they wildly diverge, Phase A was under-specified. Reframe and re-run rather than averaging the divergence.

## Phase F: Verify

Verify the synthesized artifact like any other output, per the **prove-it-works** principle skill. If verification finds a problem the arena missed, either Phase A was wrong (re-frame and re-run) or a candidate caught it and you missed the graft (go back to Phase E). Don't paper over it.

## Outputs

One synthesized artifact, with a short synthesis note alongside naming the base and why, the cross-judge's verdict or why Phase C skipped it, each graft with its source candidate, what was rejected and why, any convergence or dropouts, and the verification result.
