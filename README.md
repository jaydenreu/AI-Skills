# AI Skills

Portable, stage-specific skills for framing, planning, routing, and delivering software and knowledge work. Invoke the smallest skill that matches the current stage; do not load the whole library.

## Skills

### Routed delivery workflow

| Skill | Job | Completion artifact |
| --- | --- | --- |
| `set-the-rails` | Establish a user-confirmed tracker, source of truth, PRD location, AI routing policy, decisions, standards, review, and done rules. | Rails Contract |
| `pin-it-down` | Resolve delivery-changing ambiguity through a decision-complete interview. | Durable decisions and open-item ledger |
| `write-the-brief` | Publish accepted decisions as the canonical execution-ready PRD. | Canonical PRD |
| `slice-the-work` | Create vertical issues and route every accepted issue with `$model-route`. | Ordered routed issues |
| `deliver-the-slice` | Execute one routed issue, validate, review, and record completion. | Verified outcome and completion record |

### Universal workflow

| Skill | Job | Completion artifact |
| --- | --- | --- |
| `orient-the-field` | Establish operating context for any endeavor. | Context contract and next action |
| `clarify-the-aim` | Resolve action-changing ambiguity. | Durable decisions and ambiguity ledger |
| `explore-the-terrain` | Compare evidence, options, tradeoffs, and probes. | Terrain map and recommendation |
| `shape-the-brief` | Turn resolved context into an action brief. | Brief with evidence and first step |
| `carve-the-path` | Break large work into verifiable steps. | Ordered AFK/HITL path |
| `carry-the-step` | Complete one focused step with proof. | Verified result and durable record |
| `arrange-the-space` | Reduce workspace friction and define reset defaults. | Workspace layout and reset routine |
| `practice-the-skill` | Build ability through deliberate practice. | Practice loop and progression gate |
| `stress-test-the-plan` | Pressure-test assumptions, dependencies, risks, and failure modes. | Resolved decisions and residual risks |

### Model routing

| Skill | Job | Completion artifact |
| --- | --- | --- |
| `$model-route` | Assign GPT-5.6 models, reasoning, agents, review, and validation by task intensity. | Compact or full execution route |

The maintained Luna/Terra/Sol and T0–T5 map lives in [`model-route/SKILL.md`](skills/ai/model-route/SKILL.md). Volatile pricing and availability are conditional reference material, not part of the routine routing path.

## Composition

Recommended routed delivery:

```text
set-the-rails → pin-it-down → write-the-brief → slice-the-work
               → $model-route Recommend → deliver-the-slice
```

`write-the-brief` publishes the canonical PRD consumed by `slice-the-work`. `set-the-rails` records the applicable AI routing policy or explicit use of `$model-route` defaults; it does not route work.

`slice-the-work` invokes `$model-route` once for the accepted slice set and writes a route into every published issue. `deliver-the-slice` consumes that route and refreshes it only when missing, pending, materially stale, or invalidated by changed requirements. This is the library's only required cross-skill integration.

Recommended universal path:

```text
orient-the-field → clarify-the-aim and/or explore-the-terrain
                 → shape-the-brief → carve-the-path → carry-the-step
```

Skip any stage whose artifact already exists and is trustworthy. `arrange-the-space`, `practice-the-skill`, and `stress-test-the-plan` enter wherever their specific job is needed.

The paired skills are deliberate specializations, not dependencies:

- `orient-the-field` is universal; `set-the-rails` is delivery-governance specific.
- `clarify-the-aim` is broad; `pin-it-down` is the stricter delivery gate.
- `shape-the-brief`/`carve-the-path`/`carry-the-step` are universal; `write-the-brief`/`slice-the-work`/`deliver-the-slice` produce tracker-ready routed delivery artifacts.

## Invocation policy

The five delivery workflow skills and `model-route` are explicit-only through `agents/openai.yaml`. Universal skills may be invoked from their trigger descriptions. Every skill remains independently usable except the intentional routed-issue handoff described above.

## Authoring rule

Keep each `SKILL.md` to its irreducible procedure and checkable completion gate. Default budgets are 250 words for an ordinary skill and 900 for `model-route`; exceed them only when a behavior cannot be disclosed conditionally. Put volatile or branch-only facts behind conditional references, keep one source of truth per rule, and remove examples or prose that do not change behavior. Validate every changed skill and forward-test material workflow changes.
