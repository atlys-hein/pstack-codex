# Skill resources

Start with [this skill](SKILL.md), then read [Ketchup](../ketchup/SKILL.md). The [shared Codex contract](../pstack/CODEX.md) owns execution rules, and the [package index](../pstack/INDEX.md) lists active skills.

This is an instruction-only workflow. It packages no video renderer. Detect the available frame renderer and encoder, such as FFmpeg plus ffprobe, from the current runtime. Validate the actual video and representative frames before presenting a result; report renderer absence or render failure without claiming success.

Ported from [cursor/plugins, ketchup-video](https://github.com/cursor/plugins/tree/c742dd61706fbacc1b95f1a20b7b988cf096ce6c/pstack/skills/ketchup-video) at commit `c742dd61706fbacc1b95f1a20b7b988cf096ce6c` (0.15.36), under the package's upstream license and notices. Preserve those root notices when redistributing this skill. Codex changes adapt invocation and supported history/media tools, local artifact paths, renderer detection, and actual-file validation. Ordinary implicit invocation remains enabled.
