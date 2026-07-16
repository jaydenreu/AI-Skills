# AI Skills

This repository contains portable skills for framing, planning, delivering, and routing work across software, analytics, research, documentation, product, operations, and other knowledge work.

The skills are standalone: no skill requires another one to function. The delivery order below is a recommended human workflow, not a dependency chain.

## Delivery Workflow Skills

| Skill | Use it for | Output |
| --- | --- | --- |
| `set-the-rails` | Configure how a project or workspace is managed. | Source of truth, tracker, decision log, standards, done rules. |
| `pin-it-down` | Relentlessly interview before delivery and question everything delivery-relevant. | Durable decisions, open blockers, decision IDs. |
| `write-the-brief` | Turn resolved context into an execution-ready brief. | Brief with problem, goal, non-goals, behaviour, evidence, first slice. |
| `slice-the-work` | Break a brief into small vertical slices. | Ordered AFK/HITL slices with acceptance criteria and evidence. |
| `deliver-the-slice` | Complete one slice without scope drift. | Delivered outcome, checks, evidence, review result, completion reference. |

## Universal Skills

| Skill | Use it for | Output |
| --- | --- | --- |
| `orient-the-field` | Set up operating context for a project or endeavor. | Source of truth, decision log, evidence, done rules. |
| `clarify-the-aim` | Relentlessly reduce ambiguity before action across broad work. | Durable decisions, open ambiguity, artifact expectations. |
| `explore-the-terrain` | Explore uncertain topics, options, and tradeoffs before committing. | Evidence, options, confidence, and recommended next move. |
| `shape-the-brief` | Turn resolved context and decisions into an action brief. | Outcome, boundaries, evidence, and first useful step. |
| `carve-the-path` | Break a goal or brief into small ordered steps. | Dependency-aware steps with evidence and human boundaries. |
| `arrange-the-space` | Design or reset a workspace for focused work. | Deliberate layout, materials, routines, and reset rules. |
| `carry-the-step` | Execute one focused step without scope drift. | Verified result and completion evidence. |
| `practice-the-skill` | Build ability through deliberate practice and feedback. | Practice loop, evidence, feedback, and progression. |
| `stress-test-the-plan` | Stress-test a plan or design before building. | Resolved decisions, remaining ambiguity, accepted defaults, risks, next step. |

The interview skills include their own ambiguity loops. They do not depend on an external interview skill.

`clarify-the-aim` is the broad pre-action interview for vague endeavors. `pin-it-down` is the narrower delivery gate before `write-the-brief`; it should be more ruthless because its job is to make execution unambiguous. If that distinction stops being useful, collapse to `pin-it-down` as the single interview gate.

## Model Routing and Orchestration

| Skill | Use it for | Output |
| --- | --- | --- |
| `$model-route` | Recommend, execute, or audit the lowest-cost credible model, reasoning, and concrete agent/thread route. | Exact root, explorer, writer, reviewer, model, reasoning, wave, and validation assignments. |

`model-route` is explicitly invoked. It composes after the relevant orientation, exploration, shaping, and decomposition work and before execution. It is a mandatory handoff for published issues, using a lightweight compact route for non-material T0-T1 work, and it does not replace existing execution skills.

```text
$model-route Recommend the model, reasoning effort, and agent/thread route for this task. Do not execute it.
$model-route Route and execute this bounded change. Use one writer and proportionate validation.
$model-route Audit whether the route used for this completed task was proportionate to its outcome and risk.
```

Parallel work is limited to genuinely independent streams. Overlapping implementation stays under one writer, and material work receives independent review. Current models, reasoning support, availability, credits, API prices, and the update procedure live in the [model catalogue](skills/ai/model-route/references/model-catalog.md). Organization and repository policy override its generic recommendations.

The default intensity routing is explicit:

| Intensity | Agent route | Reasoning |
| --- | --- | --- |
| T0 Exact | Root/`default`; `gpt-5.6-luna`; no child | Low/Light |
| T1 Routine | `default`, optional `explorer`, and one `worker` on `gpt-5.6-terra` | Medium |
| T2 Demanding | Terra `default`/`explorer`/`worker`; Sol reviewer if material | High writer; medium explorer; high reviewer |
| T3 Critical | `gpt-5.6-sol` lead, writer or specialist, and separate reviewer | High lead; xhigh writer; high reviewer |
| T4 Exceptional coupled | Sol root/`default` is sole writer; separate Sol reviewer | Max root; high/xhigh reviewer |
| T5 Broad independent | Sol `default` orchestrator; Luna/Terra/Sol children by stream intensity | High root; each child routed at T1-T3; Ultra only after its gate |

See the [orchestration patterns](skills/ai/model-route/references/orchestration-patterns.md#task-intensity-route-examples) for the exact agent contracts and examples.

### Issue routing lifecycle

Every issue created by `slice-the-work` carries an `Execution route`. It invokes `$model-route Recommend` after the slice is defined, stores a compact route for non-material T0-T1 work or the full manifest for T2-T5/material work, and records the model-source review date. `deliver-the-slice` consumes that route and writes the actual visible route, deviations, review, corrections, and validation back into the issue.

For managed organizational distribution, package the skill as a plugin when that becomes useful; this repository keeps it as a directly authored skill.

## Recommended Order

For a new repo, business project, client workspace, or team workflow:

```text
/set-the-rails
/pin-it-down
/write-the-brief
/slice-the-work
$model-route Recommend each accepted slice and write its execution route into the issue
/deliver-the-slice
```

For an existing project where the rails already exist:

```text
/pin-it-down
/write-the-brief
/slice-the-work
$model-route Recommend each accepted slice and write its execution route into the issue
/deliver-the-slice
```

For a ready-made issue, ticket, or slice:

```text
$model-route Recommend and write or refresh the issue's execution route
/deliver-the-slice
```

Every published slice receives a route. Use the compact form for non-material T0-T1 work and the full manifest for T2-T5 or material work before execution.

## How To Choose The Entry Point

Start with `set-the-rails` when the project machinery is unclear. Use it when no one has agreed where work lives, where decisions are recorded, what "done" means, or who reviews what.

Start with `pin-it-down` when the workflow exists but the work itself is still fuzzy. This skill should relentlessly interview, question everything delivery-relevant one question at a time, and capture durable decisions before anyone starts building.

Start with `write-the-brief` when the decisions are mostly resolved and you need a concise delivery brief. It should not restart the interview unless a missing answer would change delivery.

Start with `slice-the-work` when you have a brief or plan and need small, reviewable slices. Each slice should produce something visible or verifiable.

Start with `deliver-the-slice` when one slice is already clear enough to build, verify, review, and record as complete.

Invoke `$model-route` for every published issue and whenever model cost, reasoning depth, delegation, parallel workstreams, one-writer control, or independent-agent review needs an explicit decision. Skip it only for ordinary low-risk ad hoc work that is not represented by an issue and has no meaningful routing choice.

## Loading Guidance

Do not load every skill at once. Invoke the skill that matches the current stage of work.

Use the full sequence when moving from a blank or unclear workspace to delivery. Skip earlier skills only when their outputs already exist and are trustworthy.

When in doubt:

1. If the workflow is unclear, run `set-the-rails`.
2. If the workflow is clear but the work is unclear, run `pin-it-down`.
3. If the decisions are clear but the execution brief is missing, run `write-the-brief`.
4. If the brief is clear but the work is too large, run `slice-the-work`.
5. If a slice is clear and ready, run `deliver-the-slice`.

After decomposition, write a `$model-route` result into every issue before execution; compact routes keep T0-T1 work lightweight.

## Repo Structure

```text
skills/
  ai/
    model-route/
      SKILL.md
      agents/
        openai.yaml
      references/
        model-catalog.md
        orchestration-patterns.md
  workflow/
    set-the-rails/
      SKILL.md
    pin-it-down/
      SKILL.md
    write-the-brief/
      SKILL.md
    slice-the-work/
      SKILL.md
      agents/
        openai.yaml
    deliver-the-slice/
      SKILL.md
      agents/
        openai.yaml
  universal/
    orient-the-field/
    clarify-the-aim/
    explore-the-terrain/
    shape-the-brief/
    carve-the-path/
    arrange-the-space/
    carry-the-step/
    practice-the-skill/
    stress-test-the-plan/
```

## Design Notes

- Older workflow skills retain the repository's legacy `disable-model-invocation: true` convention; updated workflow skills migrate to current `agents/openai.yaml` policy metadata.
- `model-route`, `slice-the-work`, and `deliver-the-slice` use `allow_implicit_invocation: false`, so all three remain explicit-only.
- The pack is intentionally broad enough for non-code work and strict enough to prevent delivery drift.
- The sequence favours evidence, review, and explicit completion records over internal activity.
- Each skill should produce the smallest useful artifact for its stage.
