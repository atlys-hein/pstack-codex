---
name: "recall"
description: "Reconstruct recent working context from authorized chat history, live repository state, and relevant shared records. Use for recall my work, catch me up, or where did I leave off."
---

On resource hosts, select the target skill’s owning package from the current catalog or supported explicit selector before reading a cross-skill link; retain its provided authority and resource identifier.

Read [the Codex execution contract](../pstack/CODEX.md) before this workflow. It defines supported tools, bounded delegation, shared-checkout ownership, validation, and authorization. Use only capabilities exposed in this session.

# Recall

Rebuild the user's working context and return a tight brief of what is current and what comes next. This is read-only unless the user also asks to resume implementation.

Your chat history records prior decisions. The shared record holds user reports, shipped or reverted fixes, and continuing errors. Use **why** source playbooks for that second record when the question names a feature, subsystem, or bug.

1. Classify the request. One specific chat or branch to resume uses the Session pickup playbook. Working habits belong to **automate-me**. If the user already supplied a sufficient state capsule, use it instead of mining history.
2. Bound the scope by topic, project, and date range. Default recent to the last seven days and the active project. State any material assumption. Never silently narrow an explicit all-history request.
3. Use native chat listing and reading tools when available. Select relevant chats from their titles, retrieval summaries, project metadata, and timestamps; then read the matching turns. Skip unrelated projects and obvious test or evaluation chats. If native history access is unavailable, use an authorized export or the context already available and state the gap. Do not inspect private application databases or guess transcript paths.
4. For many relevant chats, delegate bounded read-only slices. Each worker returns the user's goal, decisions, open work, corrections, and artifacts with chat identifiers or source pointers. Apply the shared model policy before spawning. For one or two chats, inspect directly. Keep raw histories out of the aggregate report.
5. For a named technical target, search relevant shared records through available connectors, using the **why** source playbooks. Keep a category coverage map with null results and gaps. Bound searches to the topic and time range. Perform independent source work in parallel only within host capacity.
6. Verify current branches with local git, PRs with the GitHub connector or authenticated `gh` fallback, and tickets with the matching connector. A past chat's success claim is not proof of current status. If tool-level evidence is unavailable, say what cannot be verified.
7. Return the brief below. Do not resume code changes merely because the brief names a next action.

## Brief

- **Capsule.** At most five bullets describing the work and its current overall state.
- **Threads.** One line per relevant thread with an evidence-backed status, such as merged, open PR, in flight, verified but uncommitted, reverted, planned, or unknown. Do not force an unsupported status.
- **Problems.** At most five continuing symptoms, reverted fixes, or material gaps.
- **Next move.** The most useful concrete action.

Exclude adjacent work unless it blocks the target. Cite chat or artifact links when available and preserve the source's actual chat title. Use **unslop** and sanitize private context before any separately authorized public output.
