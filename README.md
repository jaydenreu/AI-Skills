# AI Skills

Portable, stage-specific skills for framing, planning, routing, orchestrating, and delivering software and knowledge work. Invoke the smallest skill that matches the current stage; do not load the whole library.

## Skills

### Entry and orchestration

Start unfamiliar repositories by selecting a workflow and checked skill path; branch accepted independent work into observable child tasks only when routing and repository policy allow it.

| Skill | Job | Completion artifact |
| --- | --- | --- |
| `start-the-work` | Choose universal, routed delivery, or universal → delivery and maintain the gated skill checklist. | Work Path with one current skill |
| `orchestrate-the-work` | Coordinate routed child tasks, dependency waves, status, integration, and return to the parent. | Verified parent outcome and thread ledger |

### Routed delivery workflow

Use this opinionated, tracker-backed path to move software from delivery governance through routed, reviewed, and traceable issues.

| Skill | Job | Completion artifact |
| --- | --- | --- |
| `set-the-rails` | Establish tracker, source of truth, Work Path, AI routing, thread authority, review, and done rules. | User-confirmed Rails Contract |
| `pin-it-down` | Resolve delivery-changing ambiguity through a decision-complete interview. | Durable decisions and open-item ledger |
| `write-the-brief` | Publish accepted decisions as the canonical execution-ready PRD. | Canonical PRD |
| `slice-the-work` | Create vertical issues, dependency waves, and routed execution containers. | Ordered routed issues |
| `deliver-the-slice` | Execute one routed issue and return validation, review, and memory evidence to its parent. | Verified outcome and parent return |

### Universal workflow

Use these composable skills for any kind of work; enter at the current stage and combine only what the endeavor needs.

| Skill | Job | Completion artifact |
| --- | --- | --- |
| `orient-the-field` | Establish operating context for any endeavor. | Context contract and next action |
| `clarify-the-aim` | Resolve action-changing ambiguity. | Durable decisions and ambiguity ledger |
| `explore-the-terrain` | Compare evidence, options, tradeoffs, and probes. | Terrain map and recommendation |
| `shape-the-brief` | Turn resolved context into an action brief. | Brief with evidence and first step |
| `carve-the-path` | Break large work into verifiable steps. | Ordered AFK/HITL path |
| `carry-the-step` | Complete one focused step with proof. | Verified result and durable record |
| `remember-the-work` | Recall prior decisions and failures, then preserve reusable lessons. | Search result and memory classification |
| `arrange-the-space` | Reduce workspace friction and define reset defaults. | Workspace layout and reset routine |
| `practice-the-skill` | Build ability through deliberate practice. | Practice loop and progression gate |
| `stress-test-the-plan` | Pressure-test assumptions, dependencies, risks, and failure modes. | Resolved decisions and residual risks |

### Model routing

| Skill | Job | Completion artifact |
| --- | --- | --- |
| `$model-route` | Assign GPT-5.6 models, reasoning, execution containers, agents, review, and validation. | Compact or full execution route |

The maintained Luna/Terra/Sol and T0–T5 map lives in [`model-route/SKILL.md`](skills/ai/model-route/SKILL.md). Volatile pricing and availability are conditional reference material, not part of routine routing.

## Composition

Use `start-the-work` as the entrypoint when the correct path or current gate is not already established:

```text
start-the-work
├─ universal → orient / clarify / explore → shape → carve → carry
├─ universal → delivery → explore / clarify → set-the-rails → routed delivery
└─ routed delivery → set-the-rails → pin-it-down → write-the-brief
                     → slice-the-work → $model-route Recommend
                     → orchestrate-the-work when child tasks are routed
                     → deliver-the-slice per issue → integrated review
```

Skip a gate only when its artifact already exists and is trustworthy. The Work Path records the evidence and keeps exactly one skill current.

`slice-the-work` routes every accepted issue through `$model-route`. `orchestrate-the-work` calls `$model-route` for the parent topology and each child, keeps the parent orchestration-only after branching, and requires every child to return status and evidence. Concurrent writers require isolated ownership and the Rails thread policy.

`remember-the-work` crosses both paths. Children return memory candidates; the reconciled parent is the sole writer of durable project memory.

The paired skills are deliberate specializations:

- `orient-the-field` is universal; `set-the-rails` is delivery-governance specific.
- `clarify-the-aim` is broad; `pin-it-down` is the stricter delivery gate.
- `shape-the-brief`/`carve-the-path`/`carry-the-step` are universal; `write-the-brief`/`slice-the-work`/`deliver-the-slice` produce tracker-ready delivery artifacts.
- `model-route` decides compute and container; `orchestrate-the-work` executes the accepted topology.

## Invocation policy

The five delivery skills and `model-route` are explicit-only through `agents/openai.yaml`. `start-the-work` is model-invoked for unfamiliar or unconfigured repositories; `orchestrate-the-work` is reachable when an accepted route requires child tasks. Child-task creation must honor the Rails Contract's thread authority.

## Authoring rule

Keep each `SKILL.md` to its irreducible procedure and checkable completion gate. Default budgets are 250 words for an ordinary skill and 900 for `model-route`; exceed them only when behavior cannot be disclosed conditionally. Put branch-only facts behind references, keep one source of truth per rule, and remove prose that does not change behavior. Validate every changed skill and forward-test material workflow changes.
