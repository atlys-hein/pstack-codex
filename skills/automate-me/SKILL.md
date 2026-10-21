---
name: "automate-me"
description: "Create or update a personal mode skill from the user's stated preferences and authorized conversation evidence. Use for automate me, capture my working style, or update my mode skill."
---

On resource hosts, select the target skill’s owning package from the current catalog or supported explicit selector before reading a cross-skill link; retain its provided authority and resource identifier.

Read [the Codex execution contract](../pstack/CODEX.md) before this workflow. It defines supported tools, bounded delegation, shared-checkout ownership, validation, and authorization. Use only capabilities exposed in this session.

# Automate me

Turn the user's working conventions into one focused `-mode` skill, such as `jay-mode`. Use the available Codex **skill-creator** skill for authoring and **unslop** for prose.

## 1. Find the existing owner

Check the active project's `.agents/skills/` and any personal skill location exposed by the session catalog for an existing matching skill. Preserve its location and conventions. A request to update it authorizes the in-scope local edits. If multiple matching skills could be the target, resolve that before editing. Do not modify the installed plugin cache as a way to persist changes.

## 2. Gather evidence

Start with explicit preferences in the current conversation and applicable `AGENTS.md`. If the user asked to learn from prior work, use native chat listing and reading tools when available, limited to the requested topic, project, and date range. Otherwise use user-provided exports or the conversation context already available. Do not search private application transcript stores or unrelated projects.

For a substantial authorized history corpus, delegate a few distinct read-only slices through native tools. Apply the shared model policy before spawning. Each returns concrete patterns with evidence pointers, contradictions, and confidence. For an update, prioritize evidence since the last edit and preserve rules the user has not contradicted.

Look for response style, delegation preferences, verification expectations, code and prose conventions, and repository process. Repeated signals are stronger than isolated behavior, but one explicit user preference is sufficient. Do not turn one mistake into a universal rule.

## 3. Fill meaningful gaps

Ask one or two focused questions only where the evidence leaves a choice that changes the result. Use the available structured input tool and its actual option limits, or a concise ordinary question. Existing authorization persists. Do not force an interview when the request is already clear.

## 4. Draft or update

Use Codex skill-authoring guidance. A new project skill normally lives at `.agents/skills/<handle>-mode/SKILL.md`; use the requested personal location for a personal skill. Use a name and description that identify this person's mode, not broad triggers such as all code work. Optional UI and invocation policy belong in `agents/openai.yaml` under the supported schema. Preserve an existing invocation policy; change it only when the user requests that behavior.

Include only specific preferences that change a future decision. Common sections are response style, autonomy, understanding first, delegation, validation, and process. Omit empty categories. Reference existing skills by path rather than copying them. The **poteto-mode** skill is an example of granularity, not a source of this user's preferences.

Keep user preferences subordinate to higher-priority instructions and runtime permissions. A mode skill cannot authorize messages, commits, PRs, installations, or external writes on unrelated tasks.

## 5. Validate and return

Apply **unslop**, verify frontmatter and links, and run an available skill validator when permitted. Subjective preferences are best checked against the evidence and the user's feedback. A practical forward test is useful for operational rules, not a compulsory benchmark loop for prose.

Return the skill path, key changes, and any unresolved preference. Commit, push, or open a PR only when requested. Suggest recurring refresh only if the user asks, using the native scheduler.

Use **skill-creator** directly for a narrow task skill rather than mining the user's habits.
