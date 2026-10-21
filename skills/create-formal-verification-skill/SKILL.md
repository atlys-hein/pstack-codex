---
name: "create-formal-verification-skill"
description: "Generate a project-local skill that formally verifies code where a bug costs the most and tests reach the least, using a tool that fits. Use for $create-formal-verification-skill, \"model-check this race\", or \"prove this invariant\" when concurrency, retries, state machines, parsers, or unsafe code need more than tests."
---

On resource hosts, select the target skill’s owning package from the current catalog or supported explicit selector before reading a cross-skill link; retain its provided authority and resource identifier.

Read [the Codex execution contract](../pstack/CODEX.md) before this workflow. It defines supported tools, validation, shared-checkout ownership, and authorization. Use only capabilities exposed in this session.

# Create a formal verification skill

A test checks the cases that someone thought to write. Formal verification checks every case in a stated scope: every order of steps in a model, every input up to a bound, or every input covered by a proof. Find the part of the repo where that matters most, verify one property of it, and leave a project-local skill that lets the next agent check a change against that property. Write that skill for an agent who reads it cold, mid-change, and has never seen your work. The user must be able to trust the result and act on it without learning the verification language.

## Scope

A request to create the skill authorizes local verification artifacts and a project-local skill, usually `.agents/skills/verify-<area>/SKILL.md`. Follow an existing repository convention when present. An audit, review, or explanation request is read-only: inspect and report proposed targets, available checks, and gaps without creating or editing files. Run a check during an audit only if it is permitted and does not change shared state.

Inspect the worktree before edits and preserve user changes. Product code changes, dependency installation, global configuration, shared-service writes, and external delivery need their own authorization. If the required tool or access is unavailable, report the specific blocker and leave an unexecuted skill marked as a draft.

## Choose the target from the code

Answer from the codebase, and ask the user only what you cannot observe. If the user named an area or a bug, start there.

A good target is a promise the code makes, where a break harms users and tests rarely reach the case that breaks it. Choose the strongest such target within the requested scope, not the one that is easiest to verify.

## Let the question choose the tool

Pick the tool that answers the question at the lowest cost: a model checker, a proof assistant, an SMT-backed verifier, or another tool. Whether events can happen in a bad order usually suits a model checker over a small model of the design, and TLA+ is the default for that in any language. Whether the code itself behaves for every input, as with memory safety, overflow, or a data-structure invariant, usually suits a verifier that runs on the code. If no verifier runs on this language, say so, and test the real code with generated inputs, not a hand model of the function. Report that fallback as testing, not a formal proof. A property that must hold at every size, where a bound is not enough, can need a proof. Prefer a tool the repo's developers can install and run, and tell the user why you chose it. Prefer an existing pinned tool and inspect its command before running it; honor repository restrictions on validation commands.

## What makes it good

- **True to the code.** Every part of the model or proof points to code that a reviewer can open. What the verification treats as one indivisible step is one indivisible step in the code. Names come from this repo.
- **Able to fail.** A check that you have never seen fail is unvalidated. Show each property failing on a broken variant of the code it guards, such as a removed check or a reordered step.
- **Findings stay findings.** When the current code breaks the property, report it with the counterexample in the code's terms. Do not weaken the property or the model until it passes, and do not change product code unless the user asks.
- **Honest about scope.** Say what is verified, under which bounds and assumptions, and what is left out. A pass covers the model or the bound, not the whole system.
- **Readable without the tool.** State the property and the harm in one plain sentence each. Tell a counterexample as a short sequence of steps in the code's words.
- **Cheap to rerun.** One command, a reproducible tool version, and a run short enough that the next agent will use it on every relevant change.
- **Kept in step with the code.** Record which files and functions each check covers, and the commit at which you last confirmed that the verification describes them. Record any covered uncommitted changes separately; a commit hash alone does not describe them.

## Generate the verify skill

Write a project-local skill with frontmatter that names the area and says when to use it. Without frontmatter, the skill never registers. From the skill alone, the next agent must be able to tell whether a change touches the verified code, run the check, tell a real bug from a modeling error, and update the verification when a change is intended. Put the coverage record and the sync commit in the skill, and tell the next agent to move the sync commit forward only after confirming that the verification describes the code at the new commit. Do not advance it for a blocked check or use it to claim uncommitted changes were checked as part of that commit. Use this repo's real commands, paths, and nouns, and leave no placeholders.

## Prove it before you hand off

Follow the generated skill once, as the next agent would, on an owned scratch copy containing the exact covered code, including relevant user changes. Make the scratch change in the real code that breaks the property; never mutate the user's working files or discard their changes. The generated workflow must catch the break. For a hand model, follow its code-to-model synchronization steps on that scratch change; a failing mutation made only to a model does not demonstrate that the workflow catches changed product code.

Then rerun the unmodified baseline copy and confirm that the check is back where it started: passing, or failing only on the findings you will report. Preserve the failure evidence and identify the scratch artifacts. Remove scratch artifacts only when cleanup is authorized. A verify skill that was never run is a draft. If the skill misses the break or a step does not run, fix the skill or the verification, not the scratch change. Report a blocked mutation check honestly rather than claiming the property has been validated.

## Hand off

Tell the user what you verified, which tool you used and why, the bounds, what the check found in plain words, how to run it, and what it does not cover. Distinguish formal results, generated-input testing, static inspection, and checks that could not run. Suggest a second target only if you found a close one. Point the user at `$maintain-formal-verification-skill` for bringing the verification back in line after changes that did not recheck it.
