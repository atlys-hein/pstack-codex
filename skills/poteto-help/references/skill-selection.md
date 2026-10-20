# Skill selection

Read this catalog when recommending a skill or resolving a close call. Read the selected skill before relying on its details.

## Pick a skill

| The user wants to | Skill |
|---|---|
| Do any non-trivial task with rigor | [`$poteto-mode`](../../poteto-mode/SKILL.md) |
| Check that the agent understood their goal and the problem before it starts | [`$in-your-own-words`](../../in-your-own-words/SKILL.md) |
| Get a deeper rewritten prompt with expert methods and an outside check, without executing its task | [`$sharpen`](../../sharpen/SKILL.md) |
| Know how code works now, or where new code should live | [`$how`](../../how/SKILL.md) |
| Know why code is shaped this way, or where a number came from | [`$why`](../../why/SKILL.md) |
| Understand a change or subsystem, explained plainly | [`$teach`](../../teach/SKILL.md) |
| Catch up on their own recent work on a topic | [`$recall`](../../recall/SKILL.md) |
| Catch up on changes and list every waiting item with enough context to decide from the reply | [`$ketchup`](../../ketchup/SKILL.md) |
| Know what a small diff could break outside itself | [`$blast-radius`](../../blast-radius/SKILL.md) |
| Settle types and module shape before code that crosses a function boundary | [`$architect`](../../architect/SKILL.md) |
| Get several attempts at one brief, merged into the best one | [`$arena`](../../arena/SKILL.md) |
| Run parallel checks over slices, or race workers, with native Codex workers | [`$swarm`](../../swarm/SKILL.md) |
| Have independent reviewers inspect a diff and try to break it | [`$interrogate`](../../interrogate/SKILL.md) |
| Explicitly request a bug fix with a failing regression test first | [`$tdd`](../../tdd/SKILL.md) |
| Apply TypeScript rules to `.ts` or `.tsx` work | [`$typescript-best-practices`](../../typescript-best-practices/SKILL.md) |
| Strip comments before review, using a reviewer that didn't write them | [`$no-comments`](../../no-comments/SKILL.md) |
| Clean AI tells out of prose | [`$unslop`](../../unslop/SKILL.md) |
| Write docs, an RFC, a README, a PR description, or a commit message to a standard | [`$technical-writing`](../../technical-writing/SKILL.md) |
| Hear the last reply again in plain words | [`$bro`](../../bro/SKILL.md) |
| Give agents a scripted way to drive the app and prove behavior | [`$create-verification-skill`](../../create-verification-skill/SKILL.md) |
| Bring a verification skill and its feature map back in line with the app | [`$maintain-verification-skill`](../../maintain-verification-skill/SKILL.md) |
| Formally verify a race, invariant, or property that tests rarely reach | [`$create-formal-verification-skill`](../../create-formal-verification-skill/SKILL.md) |
| Bring formal verification back in line with changed code and distinguish drift from bugs | [`$maintain-formal-verification-skill`](../../maintain-formal-verification-skill/SKILL.md) |
| Vet a performance number before reporting or acting on it | [`$benchmark-checklist`](../../benchmark-checklist/SKILL.md) |
| Run a large or cross-cutting change, or one to review after stepping away | [`$figure-it-out`](../../figure-it-out/SKILL.md) |
| Keep a decision log during a run, and review it afterward | [`$show-me-your-work`](../../show-me-your-work/SKILL.md) |
| Inspect current Codex capabilities and supported model settings | [`$setup-pstack`](../../setup-pstack/SKILL.md) |
| Turn their own working habits into a personal mode skill | [`$automate-me`](../../automate-me/SKILL.md) |
| Turn what a finished task taught into skill edits | [`$reflect`](../../reflect/SKILL.md) |
| Stop agents from repeating the same mistakes in this repo | [`$correct`](../../correct/SKILL.md) |
| Build a UI around a supported automation integration | [`$make-bot-ui`](../../make-bot-ui/SKILL.md) |
| Find their way around pstack | `$poteto-help` |


Read an unlisted sibling skill's description before recommending it. The `principle-*` directories contain guidance applied where relevant.

Close calls:

- **how** explains current mechanics. **why** investigates historical reasons with citations. **teach** combines them for a plain explanation.
- **arena** compares alternative attempts and synthesizes one artifact. **swarm** covers slices or a declared race and produces one report.
- **architect** settles the design before authorized implementation. A design-only request stops at the design. Add "with checkpoint" when the user wants to approve the design first.
- **interrogate** reviews the selected diff. **blast-radius** traces consequences beyond it and seeks executable evidence of the key safety claim.
- **recall** searches authorized recent history and current state. **ketchup** summarizes only this chat since the user's last message.
- **figure-it-out** designs one substantial run. The Orchestrate playbook coordinates a larger program, subject to the same permissions and host capabilities.

