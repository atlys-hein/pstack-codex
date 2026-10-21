---
name: "swarm"
description: "Run bounded parallel workers over independent slices or alternative attempts, drain their results, and return one evidenced report. Use for swarm or explicit parallel coverage."
---

On resource hosts, select the target skill’s owning package from the current catalog or supported explicit selector before reading a cross-skill link; retain its provided authority and resource identifier.

Read [the Codex execution contract](../pstack/CODEX.md) before this workflow. It defines supported tools, bounded delegation, shared-checkout ownership, validation, and authorization. Use only capabilities exposed in this session.

# Swarm

## Frame

1. State the done predicate and expected artifact or report.
2. Choose coverage, race, or mixed work. For a race, declare first passing result, rank all, or best-of before spawning.
3. Apply the shared model policy before every spawn, including its permitted models, default effort pairs and inheritance checks. A comparison across the two permitted models requires verified availability and an explicit comparison request.
4. Assign each writer exclusive files, an isolated candidate directory, or an explicit worktree. A child shares the parent's checkout by default. Separate branches in one checkout do not isolate simultaneous edits.

## Fan out

Spawn through the native tool and live schema described in the shared contract. Each brief states the goal, scope, owned output, allowed side effects, verification, and result format. Pass needed context directly or by existing artifact path. Children solve their slice and must not recursively launch the full swarm unless the parent explicitly delegates a bounded subplan.

Reports use `PASS`, `ISSUES`, or `BLOCKED`, with evidence and unresolved gaps. A proven defect report lists every confirmed issue in that slice. When comparing revisions, the brief names exact SHAs. Measurement briefs also name sample counts, sample meaning, and ordering. Workers record those in their results.

Use lifecycle and messaging tools to track work and resolve overlaps. Drain workers before integrating or validating their outputs. If a worker drops out, preserve its evidence and retry once when useful. Record any remaining coverage gap.

## Aggregate

Check actual artifacts, not only status text. A result missing required revision or measurement evidence gets one targeted follow-up. A second miss becomes a gap, never a pass. Every required coverage slice needs evidence. For a race, apply the declared selection rule and account for remaining workers safely rather than leaving them writing.

Integrate accepted work without overwriting other agents or user changes. Run the smallest permitted check of the combined result. If native delegation is unavailable, perform the bounded slices sequentially and disclose that limitation.

## Report

Return one compact result table, confirmed issues, verification, and gaps or dropouts. Include the race rule when used. Do not paste raw worker transcripts or claim independence for sequential self-review.
