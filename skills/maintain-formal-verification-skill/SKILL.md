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

Read [the complete maintenance pass](references/maintenance-pass.md) before starting either an audit or maintenance. Follow all six steps, applying edits only in maintenance mode:

1. Find the checks and establish covered code, properties, bounds, assumptions, commands, and a usable sync baseline.
2. Run each permitted check as it is before edits. A passing stale description is not proof about current code.
3. Read relevant history and covered staged and unstaged changes, including moved code and new paths to guarded state.
4. Update from current code. Change a property only for an intentional promise change supported by cited evidence.
5. Rerun and validate against real code. Passing updated checks need the scratch mutation and restored-baseline validation. Replay failing counterexamples to distinguish drift from bugs.
6. Update the verify skill and sync records only after required validation. Record covered uncommitted changes separately. Do not advance a blocked check's sync commit.

An audit reports proposed updates and validation gaps without applying them. The reference defines the classification, scratch validation, counterexample, and sync-record requirements for each branch.

## Report

Tell the user, for each check:

- the outcome, commits read, and any covered uncommitted changes;
- what changed or should change in the verification and why: the code changed shape, or the promise changed on purpose with cited evidence;
- the rerun result, and the real-code break used to show the updated workflow can still fail, or why that validation was blocked;
- each bug in plain words: the counterexample as steps in the code's words, the harm, and the introducing commit when established;
- what the verification still does not cover, including new code it should cover and does not.

Say outright which failures were verification drift and which were bugs in the code. For a check that passed before an update and fails after it, say that the old pass was on a stale description. Distinguish executed verification from static inspection and unavailable checks.

Keep verification updates separate from any product fix. Return the local changes and evidence; committing or publishing them requires authorization.
