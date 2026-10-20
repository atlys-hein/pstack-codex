# Eval

Read the [Codex execution contract](../../pstack/CODEX.md). The parent owns experiment design, blinding, execution, and interpretation. The purpose is to test observable behavior before promoting a skill or prompt change.

## Blinding

- Construct candidate-facing prompts and directory names as ordinary project work. Do not label them as an evaluation, experiment, judge, rubric, score, comparison, or candidate. Preserve normal project files that the real task needs.
- Give candidates the user goal and necessary raw artifacts. Keep expected answers, hypotheses, judge criteria, variant labels, and other candidates out of their context.
- Use a fresh agent with minimal history when the native API supports it. If the runtime necessarily exposes the parent's experiment context or shared artifacts, state that blinding is incomplete. Do not claim independent blinding merely from different agent IDs.
- Ask for ordinary implementation notes and evidence, not hidden reasoning or a list of principles the agent claims it followed.
- The judge receives sanitized output labels and a rubric, never model names or the preferred result. One judge compares variants on the same scale.

## Procedure

1. Name the changed instruction and the behavior that should improve. Write a short rubric with concrete observable criteria for the judge. Include regressions and task completion, not just the behavior the new prose asks for.
2. Prepare separate permitted working directories or actual worktrees with comparable starting artifacts. Put the assigned variant where an ordinary task would discover it. Keep writable files, ports, and other resources separate. Do not modify globally installed skills or settings.
3. Author one ordinary user request and use it consistently. Change only the intended variant. Keep runtime capabilities and model settings comparable under the shared model policy. Use variation between the two permitted models only when explicitly requested, supported and relevant to the question.
4. Run a bounded number of independent workers through native agents. Use **arena** when its comparison method fits. Respect runtime capacity and cost. If agents or sufficient isolation are unavailable, perform a limited direct dry run and report what it cannot establish.
5. Have an independent judge inspect the outputs and evidence against the hidden rubric when supported. Code, produced artifacts, executed checks, and observable actions carry more weight than a candidate's claims.
6. Verify instruction-following from task-scoped tool histories or execution records only when the host exposes them. Do not search private transcript stores or unrelated chats. If those records are unavailable, report process compliance as unknown and grade the observable artifacts.
7. Inspect the important outputs yourself. Resolve disagreements by evidence or clarify an ambiguous rubric. Re-run only when a meaningful confound or change warrants it. Keep every conclusion bounded by the tested requests and conditions.

Reply with the tested variant, rubric, per-output findings, judge verdict, limitations of blinding and coverage, and whether the evidence supports promotion.
