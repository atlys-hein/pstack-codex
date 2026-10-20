# Multi-phase or multi-PR plan

Read the [Codex execution contract](../../pstack/CODEX.md). The deliverable is an executable, reviewable plan. Do not begin the implementation or publish PRs under a plan-only request.

1. Inspect scope and decide the appropriate size. A one-file change with an obvious approach may need a short plan rather than a program document. Explain that choice and still provide the requested planning outcome.
2. Resolve factual questions from source and available evidence. Use bounded read-only workers for independent subsystem questions. They return file pointers, contracts, permitted validation commands, and uncertainty. Run a prototype only when the planning request authorizes that local experiment; otherwise record the unproven assumption and the proposed experiment.
3. Choose the execution workflow from [Autonomous run](autonomous-run.md), [Autopilot-full](autopilot-full.md), [Autopilot-stack](autopilot-stack.md), or [Orchestrate](orchestrate.md). Define who owns implementation, integration, review, and any authorized landing. A multi-phase local change need not become a multi-PR program.
4. Use the template below, scaling it to the task. Give each unit one coherent change and its own observable acceptance criteria. Name dependencies, file ownership, shared resources, and blocking prerequisites. Every completed box needs an evidence artifact or an explicit not-applicable reason.
5. Write with **technical-writing** and **unslop**. Keep the body as instructions for the future owner. Put alternatives, rationale, and unresolved risks in appendices. Save in the requested location or the permitted task deliverable area, not a guessed agent store.
6. Validate the plan directly against the source and available runtime. Check file and tool references, dependency order, ownership collisions, authorization boundaries, the measurement design, and completion evidence. No fixed-number worker script or platform-specific scheduler is required.
7. Hand back the plan and its validation result. Execution begins only when requested or already included in the user's task. A persistent schedule is a separate explicit request that uses the supported automation tool.

## Verification design

Specify proof for each unit's actual risk. Behavior changes need observable runtime or public-interface evidence when available. Structural changes need an equivalence pin. Documentation changes need correctness, links, and relevant package checks. A skipped or blocked required proof is not a pass.

For a user-facing change, name the real surface, supported driver, initial state, input, expected end state, and receipt. Include a regression scenario against the base when it exists. If the base lacks the feature, say so and test the new behavior plus the end state the user waits for. Do not invent a baseline result.

For a performance-sensitive unit, name the metric, workload, baseline, interleaved probe, samples, completed work and error counts, and a failure threshold. Both sides must measure comparable work. If the feature does not exist on the base, use an absolute budget for the added work and end-to-end state rather than a ratio between unlike scenarios.

Choose verification lanes by distinct risks and run them within the host's capacity. Apply the shared model policy before spawning. Do not require ten workers, a particular cloud environment, screenshots for a nonvisual API, or a performance experiment for prose. Mark an irrelevant category with a concrete reason. Preserve every user-requested human review gate. Additional approval is needed only where the actual request or governing instructions require it.

## Plan template

```markdown
# <Program> plan

<What changes, for whom, the invariant preserved, and the units in dependency order.>

## How to read this

One box is one unit of work. Each box names the evidence that completes it.
Check a box only when its evidence exists. A blocked required check remains open.
Use <resolved execution-playbook path>. <Ownership and authorized delivery scope.>

## Program checklist

### Prepare the work

- [ ] Confirm the requested outcome, constraints, completion predicate, and user gates.
- [ ] Read applicable repository instructions and the relevant installed playbooks.
- [ ] Record the actual base ref, current worktree state, and unrelated edits.
- [ ] Resolve <blocking prerequisites> before assigning dependent units.
- [ ] Record <concurrency limit, available native tools, ownership, and permitted checks>.
- [ ] If persistent scheduling was explicitly requested, create it through the supported tool with <predicate, cadence, and meaningful-change notification rule>. Otherwise use in-session waits and a resume checkpoint.
- [ ] On a user hold, stop new work and propagate the hold to every active owner.

### Assign owners

- [ ] <Unit> owns <paths/resources> in <worktree or shared-checkout boundary>.
- [ ] <Unit> depends on <accepted output or parent head> from <unit>.
- [ ] Give each worker current constraints, acceptance criteria, allowed checks, and a report shape.
- [ ] Keep implementation writers separate from independent review where warranted.

### Delivery and integration

- [ ] <Local integration, authorized commit/PR workflow, or authorized landing rule>.
- [ ] Run only the applicable permitted checks; preserve hooks and user restrictions.
- [ ] For PRs, verify the actual base, current head, review state, and attached URL.
- [ ] Bind each verdict to the checked head and base; reassess after either changes.
- [ ] Preserve user gates and the single owner of any stack topology.

### Verification setup

- [ ] <Available driver or test command and target surface>.
- [ ] <Environment, data, dependencies, and ready signal>.
- [ ] <Isolation for files, ports, browsers, databases, or other shared resources>.
- [ ] Save evidence to <permitted artifact location> and return paths with outcomes.

## <Task as a verb phrase> (<unit id>)

**Depends on.** <Unit id and required output, or None.>

**Ownership.** <Writer, paths, forbidden paths, and shared-resource constraints.>

**Build.**

- [ ] <Concrete change to a symbol, contract, or artifact>.

**Observable result.**

- [ ] <Input and expected user-visible or public-interface output>.

**Verify behavior or equivalence.**

- [ ] Run <permitted command or scenario> at <head/base or artifact>. Pass when <predicate>. Save <evidence>.
- [ ] Check <regression scenario> against <comparable baseline, or explain why none exists>.

**Verify runtime.** <Required scenarios, or not applicable with a reason.>

- [ ] <Scenario, supported driver, initial state, input, expected end state, and receipt>.

**Verify performance.** <Metric, probe, measured baseline, samples, work/error counts, and failure threshold, or not applicable with a reason.>

**Review gate.** <User-required gate and evidence, or no additional approval required.>

**Deliver.**

- [ ] Review the complete unit diff and validate its acceptance criteria.
- [ ] <Integrate locally, return an artifact, publish the authorized PR, or perform the authorized merge>.
- [ ] Record <exact head/base, verdict, evidence, and actual delivery state>.

## Close the program

- [ ] Reconcile every unit and active worker with evidence or an explicit blocker.
- [ ] Confirm the final artifact meets the completion predicate.
- [ ] Report completed work, executed checks, remaining limits, and artifact links.

## Appendix A. Evidence and experiments

<Questions resolved by source or permitted experiments, artifact paths, and unproven assumptions.>

## Appendix B. Alternatives

<Material alternatives and why the chosen approach fits the constraints.>

## Appendix C. Risks and decisions

<Each risk, owning unit, mitigation or observation, and any user decision required.>

## Appendix D. Sources

<Verified repository paths, official documentation, relevant skills, and decision trail.>
```

Reply with the plan path, unit dependencies, explicit review or authorization gates, what the evidence establishes, and the plan checks actually performed.
