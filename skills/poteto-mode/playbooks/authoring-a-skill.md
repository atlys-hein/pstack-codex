# Authoring or modifying a skill

Read the [Codex execution contract](../../pstack/CODEX.md). The deliverable is a useful Codex skill whose scope, tools, and supporting files match the target host.

1. Read the existing skill, its references and callers, and the applicable repository instructions. Use Codex's available **skill-creator** guidance. For plugin changes, also use the available plugin-authoring guidance and official OpenAI plugin documentation.
2. Identify the decisions the skill should change. Keep the entrypoint focused on purpose, routing, and essential constraints. Move substantial conditional procedures to linked references. Do not replace specific workflow knowledge with generic instructions or copy entire external manuals.
3. Match actual Codex capabilities. Check tool names and schemas against the host. Use native agents for delegation, follow the shared model policy, and preserve scope and authorization. A prompt file cannot register a runtime tool or agent type by itself.
4. Validate frontmatter, names, relative links, resource paths, supported metadata, and package boundaries. Use an available skill validator when it fits and is permitted. Inspect executable resources before retaining or changing them. Do not install into global directories as part of authoring unless requested.
5. For a substantial behavioral change, use a bounded independent forward test when native agents are available. Give the evaluator an ordinary request, the skill, and only the raw inputs needed. Check the actual outcome, not whether it repeats the intended instructions. A text-only edit needs only the relevant structural and editorial checks.
6. Review the final diff and state the scope of validation. Open a PR only if the task authorizes it, following [Opening a PR](opening-a-pr.md).

Keep only prose that changes a decision. Explain a rule when its constraint would otherwise be unclear. Point at existing types, metadata, and validation instead of repeating the same instruction across files.

Reply with the skill's purpose, material design choices, changed resources, and validation evidence.
