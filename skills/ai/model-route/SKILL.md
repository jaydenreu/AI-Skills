---
name: model-route
description: Assign GPT-5.6 models, reasoning, agents, review, and validation to a task or issue.
---

# Model Route

Choose the lowest-cost credible route for the accepted outcome and risk. Organization policy, applicable `AGENTS.md`, and the accepted source of truth override these defaults. Default to **Recommend** and stop after routing; execute or audit only when explicitly requested.

## Maintained GPT-5.6 map

**Reviewed:** 2026-07-16. This static map is intentionally maintained in the skill.

| Model | Identifier | Default use |
| --- | --- | --- |
| GPT-5.6 Luna | `gpt-5.6-luna` | Exact, repeatable T0 work |
| GPT-5.6 Terra | `gpt-5.6-terra` | Routine/demanding T1–T2 work |
| GPT-5.6 Sol | `gpt-5.6-sol`; `gpt-5.6` aliases Sol | Critical T3, coupled T4, and broad T5 work |

Use low/Light for exact work, medium for routine work, high for demanding reasoning or review, `xhigh` for critical writing, Max for one exceptional coupled problem, and Ultra only for valuable independent workstreams.

Read [model-catalog.md](references/model-catalog.md) only when the route depends on current prices, credits, surface availability, organization overrides, or model facts whose review date may be stale. Read [orchestration-patterns.md](references/orchestration-patterns.md) only before spawning agents, route-and-execute work, or an audit. Use [routing-evals.md](references/routing-evals.md) only when maintaining or testing this skill.

## Route

1. Read the task or issue, source of truth, outcome, constraints, risk, coupling, validation, dependencies, and existing route.
2. If a consequential source-of-truth choice is unresolved, return `pending` with the exact blocker.
3. Select one intensity and explicit route:

| Intensity | Use | Root / writer | Discovery | Reviewer |
| --- | --- | --- | --- | --- |
| **T0 Exact** | Local, mechanical, deterministic | `default` root/writer · Luna · low | None | Exact checks only |
| **T1 Routine** | Settled bounded work | `default` · Terra · medium; optional one `worker` · Terra · medium | Optional `explorer` · Terra · low/medium | Sol · high only if material |
| **T2 Demanding** | Bounded, cross-file or context-heavy | `default` and one `worker` · Terra · high | `explorer` · Terra · medium | Sol · high if material |
| **T3 Critical** | Security, privacy, access, finance, governed data, migration, or consequential ambiguity | `default` · Sol · high; exactly one `worker`/custom writer · Sol · xhigh | Terra/medium for inventory; Sol/high for consequential judgment | Independent custom reviewer or fresh read-only `default` · Sol · high |
| **T4 Coupled** | One exceptional problem requiring one coherent model | Root `default` is sole writer · Sol · Max | Optional `explorer` · Terra · medium | Independent Sol · high/xhigh |
| **T5 Independent** | Several genuinely independent streams plus synthesis | `default` orchestrator · Sol · high; Ultra only when justified; writers individually routed T0–T3 | One `explorer` per useful stream | Independent integrated reviewer · Sol · high |

4. Mark `Material: yes` when failure can affect shared/production behavior, security, privacy, access, finance, governed data, compliance, availability, or integrity; when work is destructive, hard to reverse, a migration/backfill, or changes a shared interface, policy, architecture, definition, or source of truth; when verification is weak; or when policy requires review. Critical work is at least T3. Other material T1–T2 work requires independent Sol/high review.
5. Inspect exposed agents. Use built-in `default` for orchestration/synthesis, `explorer` for read-only discovery, and `worker` for bounded writes. Use a custom agent only by its visible configured name; never invent one.
6. Delegate only when independent work, specialization, isolation, or review repays coordination. Parallelize read-only discovery; keep overlapping files, state, interfaces, or decisions under one writer. Material work gets a reviewer independent of the writer.
7. Record model/reasoning settings as **intended**, **configured**, **actual visible**, or **not verifiable**. Never infer hidden runtime facts.

## Issue route

For non-material T0–T1 work, use one line:

```text
Route: routed | compact | <T0/T1> | material: no | reviewed: <date>; models: <review date> | root/writer: <agent · model · reasoning> | discovery/reviewer: <none or assignment> | validation: <checks>
```

For T2–T5 or material work, use:

```md
## Execution route
Status: routed | pending
Detail: full
Intensity / materiality: <T#> | <yes/no — rationale>
Reviewed / model source: <date> | <review date>
Source of truth / risk: <refs and material risk>
Root: <agent · model · reasoning>
Discovery: <none or assignments>
Writer: <agent · model · reasoning>
Reviewer: <none or independent assignment>
Parallelism: <none or dependency waves>
Validation: <evidence and checks>
```

Write the route into an authorized issue; otherwise return the exact publishable block. `slice-the-work` batches accepted slices through Recommend. `deliver-the-slice` consumes the route and records actual execution, deviations, review, validation, and acceptance safety.

Finish Recommend when every role, model, reasoning level, review requirement, and validation assignment is explicit and execution has not started. For explicit Route and execute or Audit modes, follow the conditional orchestration reference and report unknown runtime facts honestly.
