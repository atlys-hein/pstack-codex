---
name: "maintain-formal-verification-skill"
description: "Bring a project's formal verification back in line with code changes. Find changes to verified code, update its model, harness, or properties, rerun, and distinguish verification drift from code bugs. Use for $maintain-formal-verification-skill, \"is the model still true to the code\", or after merges and refactors that skipped rechecking."
---

Read [the Codex execution contract](../pstack/CODEX.md) before this workflow. It defines supported tools, validation, shared-checkout ownership, and authorization. Use only capabilities exposed in this session.

# Maintain a formal verification skill

A formal check proves a property of what it describes. When the code changes and the verification does not, the check can keep passing while it describes code that no longer exists. That pass is dangerous because it looks like a proof. This is the upkeep loop for a verify skill that `$create-formal-verification-skill` generated, or any project-local skill that runs a model checker, prover, or code-level verifier against named code. The project-local skill handles a change that an agent makes while using it. This skill handles the changes that skipped it: merges, edits made without the skill, and drift across many commits.

## Choose audit or maintenance

An audit or review request is read-only. Inspect the verification, covered code, history, and available evidence, then report proposed changes and each check's state. Do not apply updates or change shared application state. Run a check only if it is permitted and does not change shared state; report any gaps that need edits, mutation testing, installation, or unavailable access.

A request to maintain, update, or fix the verification authorizes local changes to its models, harnesses, property files, and verify skill. Product changes, dependency installation, global configuration, shared-service writes, commits, pushes, and external delivery need their own authorization. Inspect the worktree before editing and preserve user changes.

## Outcomes

Report each check's state and whether an update was applied:

- **in sync**: no change since the last sync alters what the check describes, and the check passes.
- **updated**: the code changed, the verification now describes the new code, and the check passes.
- **drift**: the verification no longer describes the code and has not been corrected, as in a read-only audit. State the mismatch and the proposed correction.
- **bug**: the verification describes the current code, and the code breaks the property. This is a finding about the code. It is not drift.
- **blocked**: the check could not be brought back in line, could not run, or could not complete the required validation. Say exactly why.

A check can be both updated and bug: the update makes the verification describe the code again, and then the property fails on it. Static inspection alone cannot establish a passing outcome. If there is confirmed drift or a supported bug and also a blocked check, report both facts without presenting the check as validated.

## Edit scope

Edit only the verification: models, harnesses, property files, and the verify skill itself. Never edit product code during a run unless the user asks. Mutation checks use owned scratch copies of the real code, preserving relevant user changes. When a property fails on the current code, do not weaken the property or the model to make it pass. Report the failure.

## Pass

1. **Find the checks.** A verify skill has no fixed name, so find it by what it does: a project skill, usually under `.agents/skills/`, that runs a model checker, prover, or another verifier against named code. Read each one in scope, or the one the user named. For each check, collect the property, the code it covers, the bounds and assumptions, the command that runs it, and the commit where it was last confirmed to describe the code. If no verify skill exists, stop and point at `$create-formal-verification-skill`. If the skill does not record a sync commit, use the last commit that changed the verification files, and say that you did. If there is no usable history, report that gap rather than inventing a baseline.

2. **Run it as it is.** Inspect the command and run each permitted check once before changing anything, recording the result. Honor repository restrictions on validation commands. Do not install tools or change configuration to make it run without authorization. A pass here does not tell you that the current code is correct; it tells you that the old description still holds. A failure can be drift or a bug. Do not decide which until step 5. If execution is unavailable, continue useful source inspection and report the execution gap.

3. **Read every change to covered code.** Diff the covered files from the sync commit to the current commit, read each relevant commit message, and inspect covered staged and unstaged changes separately. Also look for code that moved: a covered function that is renamed, split, or moved to another file is still covered code. Look for new code that touches the state a check guards, such as a new function that writes the same fields. For each change, decide which it is:
   - **No effect.** The change does not alter anything the verification describes, such as formatting, comments, or paths it does not cover. Check this against the model or harness, not the commit message.
   - **The verification no longer describes the code.** A step that was one indivisible action is now two, a branch was added or removed, a check moved, a new path reaches the guarded state, or a value now has a different range. The model or harness must change.
   - **The promise changed on purpose.** The change alters what the code promises, and evidence says this is intended: the doc comment, tests, changelog, or commit message. The property must change, and you must cite that evidence.
   - **The promise may be broken.** The code changed, and no evidence says the promise changed. Treat a failure that follows as a bug candidate.

4. **Update from the code, not from the result.** During maintenance, change the model or harness so each changed part again points to code a reviewer can open, and keep one indivisible step in the code as one step in the verification. Write the update from the code before rerunning, and do not shape it by what makes the check pass. Change a property only for a promise that changed on purpose. Record the old wording, the new wording, and the evidence. Keep the bounds unless the change makes them wrong. If a bound must be reduced, say so in the report. During an audit, report the proposed update without applying it.

5. **Rerun and judge each result.**
   - **Pass:** the check can pass on a description that has lost its ability to fail. In an owned scratch copy, break the new real code the way the property guards against, such as removing a new check or reordering a new step, and confirm that the generated workflow catches it. For a hand model, follow its code-to-model synchronization steps on the scratch change; mutating only the model is not evidence that it catches changed product code. Rerun an unmodified baseline copy to confirm the original result is restored. Preserve failure evidence and do not discard user changes. If this validation cannot run within the authorized scope, report it as blocked.
   - **Fail:** replay the counterexample against the real code step by step. If a step cannot happen in the code, the verification is wrong. During maintenance, fix the verification and say what was wrong; during an audit, report the drift. If every step can happen, it is a bug. Identify the introducing commit when history supports it, or state that the origin is unknown or uncommitted. Tell the counterexample as steps in the code's words, and state the harm in one sentence. If a cheap permitted test or reproduction against a scratch copy of the real code shows the bug, include it as evidence. Do not commit a reproduction to product code.

6. **Update the verify skill.** During maintenance, update the code each check covers, commands, bounds, assumptions, and sync commit. Advance the sync commit only after confirming the verification describes that committed snapshot and completing the check's required validation; a verified bug can be recorded at that snapshot with its failing result. Do not advance it for a blocked check. Record covered uncommitted changes separately and do not claim their content is described by the commit hash. Then follow the verify skill once as the next agent would, so its steps are known to run. An audit proposes these record changes without applying them.

## Report

Tell the user, for each check:

- the outcome, commits read, and any covered uncommitted changes;
- what changed or should change in the verification and why: the code changed shape, or the promise changed on purpose with cited evidence;
- the rerun result, and the real-code break used to show the updated workflow can still fail, or why that validation was blocked;
- each bug in plain words: the counterexample as steps in the code's words, the harm, and the introducing commit when established;
- what the verification still does not cover, including new code it should cover and does not.

Say outright which failures were verification drift and which were bugs in the code. For a check that passed before an update and fails after it, say that the old pass was on a stale description. Distinguish executed verification from static inspection and unavailable checks.

Keep verification updates separate from any product fix. Return the local changes and evidence; committing or publishing them requires authorization.
