# AI Skills

This repo contains a very general five-skill workflow pack for taking work from an unclear idea to a verified delivery slice.

The skills are designed for software, business, analytics, operations, and project work. They are standalone skills: no skill requires another one to function. The order below is the recommended human workflow, not a dependency chain.

## Skills

| Skill | Use it for | Output |
| --- | --- | --- |
| `set-the-rails` | Configure how a project or workspace is managed. | Source of truth, tracker, decision log, standards, done rules. |
| `pin-it-down` | Interview before delivery and remove ambiguity. | Durable decisions, open blockers, decision IDs. |
| `write-the-brief` | Turn resolved context into an execution-ready brief. | Brief with problem, goal, non-goals, behaviour, evidence, first slice. |
| `slice-the-work` | Break a brief into small vertical slices. | Ordered AFK/HITL slices with acceptance criteria and evidence. |
| `deliver-the-slice` | Complete one slice without scope drift. | Delivered outcome, checks, evidence, review result, completion reference. |

## Universal Interview Skills

| Skill | Use it for | Output |
| --- | --- | --- |
| `stress-test-the-plan` | Stress-test a plan or design before building. | Resolved decisions, remaining ambiguity, accepted defaults, risks, next step. |
| `clarify-the-aim` | Resolve ambiguity before action across broad work. | Durable decisions, open ambiguity, artifact expectations. |
| `orient-the-field` | Set up operating context for a project or endeavor. | Source of truth, decision log, evidence, done rules. |

The interview skills include their own ambiguity loops. They do not depend on an external interview skill.

## Recommended Order

For a new repo, business project, client workspace, or team workflow:

```text
/set-the-rails
/pin-it-down
/write-the-brief
/slice-the-work
/deliver-the-slice
```

For an existing project where the rails already exist:

```text
/pin-it-down
/write-the-brief
/slice-the-work
/deliver-the-slice
```

For a ready-made issue, ticket, or slice:

```text
/deliver-the-slice
```

## How To Choose The Entry Point

Start with `set-the-rails` when the project machinery is unclear. Use it when no one has agreed where work lives, where decisions are recorded, what "done" means, or who reviews what.

Start with `pin-it-down` when the workflow exists but the work itself is still fuzzy. This skill should challenge assumptions, ask one question at a time, and capture durable decisions before anyone starts building.

Start with `write-the-brief` when the decisions are mostly resolved and you need a concise delivery brief. It should not restart the interview unless a missing answer would change delivery.

Start with `slice-the-work` when you have a brief or plan and need small, reviewable slices. Each slice should produce something visible or verifiable.

Start with `deliver-the-slice` when one slice is already clear enough to build, verify, review, and record as complete.

## Loading Guidance

Do not load every skill at once. Invoke the skill that matches the current stage of work.

Use the full sequence when moving from a blank or unclear workspace to delivery. Skip earlier skills only when their outputs already exist and are trustworthy.

When in doubt:

1. If the workflow is unclear, run `set-the-rails`.
2. If the workflow is clear but the work is unclear, run `pin-it-down`.
3. If the decisions are clear but the execution brief is missing, run `write-the-brief`.
4. If the brief is clear but the work is too large, run `slice-the-work`.
5. If a slice is clear and ready, run `deliver-the-slice`.

## Repo Structure

```text
skills/
  workflow/
    set-the-rails/
      SKILL.md
    pin-it-down/
      SKILL.md
    write-the-brief/
      SKILL.md
    slice-the-work/
      SKILL.md
    deliver-the-slice/
      SKILL.md
  universal/
    stress-test-the-plan/
      SKILL.md
    clarify-the-aim/
      SKILL.md
    orient-the-field/
      SKILL.md
```

## Design Notes

- The skills are user-invoked with `disable-model-invocation: true`.
- The pack is intentionally broad enough for non-code work and strict enough to prevent delivery drift.
- The sequence favours evidence, review, and explicit completion records over internal activity.
- Each skill should produce the smallest useful artifact for its stage.
