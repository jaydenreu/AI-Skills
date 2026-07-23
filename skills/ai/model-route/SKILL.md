---
name: model-route
description: Assign GPT-5.6 models, reasoning, execution containers, agents, review, and validation to a task or issue.
---

# Model Route

Choose the lowest-cost credible route for the accepted outcome and risk. Apply organization policy, applicable `AGENTS.md`, any Rails Contract AI routing policy, and the accepted source of truth before these defaults. Default to **Recommend** and stop after routing; `$orchestrate-the-work` owns execution.

## Maintained GPT-5.6 map

**Reviewed:** 2026-07-16. This static map is intentionally maintained in the skill.

| Model | Identifier | Default use |
| --- | --- | --- |
| GPT-5.6 Luna | `gpt-5.6-luna` | Exact, repeatable T0 work |
| GPT-5.6 Terra | `gpt-5.6-terra` | Routine/demanding T1–T2 work |
| GPT-5.6 Sol | `gpt-5.6-sol`; `gpt-5.6` aliases Sol | Critical T3, coupled T4, and broad T5 work |

Use low/Light for exact work, medium for routine work, high for demanding reasoning or review, `xhigh` for critical writing, Max for one exceptional coupled problem, and Ultra only for valuable independent workstreams.

Read [model-catalog.md](references/model-catalog.md) only when the route depends on current prices, credits, surface availability, organization overrides, or model facts whose review date may be stale. Read [orchestration-patterns.md](references/orchestration-patterns.md) when assigning multiple agents or auditing orchestration. Use [routing-evals.md](references/routing-evals.md) only when maintaining or testing this skill.

## Route

1. Read applicable policy, then the task or issue, source of truth, outcome, constraints, risk, coupling, validation, dependencies, and existing route.
2. If a consequential source-of-truth choice is unresolved, return `pending` with the exact blocker.
3. Select one intensity and explicit route:

| Intensity | Use | Root / writer | Discovery | Reviewer |
| --- | --- | --- | --- | --- |
| **T0 Exact** | Local, mechanical, deterministic | `default` root/writer · Luna · low | None | Exact checks only |
| **T1 Routine** | Settled bounded work | `default` · Terra · medium; optional one `worker` · Terra · medium | Optional `explorer` · Terra · low/medium | Sol · high only if material |
| **T2 Demanding** | Bounded, cross-file or context-heavy | `default` and one `worker` · Terra · high | `explorer` · Terra · medium | Sol · high if material |
| **T3 Critical** | Security, privacy, access, finance, governed data, migration, or consequential ambiguity | `default` · Sol · high; exactly one `worker`/custom writer · Sol · xhigh | Terra/medium for inventory; Sol/high for consequential judgment | Independent custom reviewer or fresh read-only `default` · Sol · high |
| **T4 Coupled** | One exceptional problem requiring one coherent model | Root `default` is sole writer · Sol · Max | Optional `explorer` · Terra · medium | Independent Sol · high/xhigh |
| **T5 Independent** | Several genuinely independent streams plus synthesis | `default` parent orchestrator · Sol · high; Ultra only when justified; writers individually routed T0–T3 | One `explorer` per useful stream | Independent integrated reviewer · Sol · high |

4. Mark `Material: yes` when failure can affect shared/production behavior, security, privacy, access, finance, governed data, compliance, availability, or integrity; when work is destructive, hard to reverse, a migration/backfill, or changes a shared interface, policy, architecture, definition, or source of truth; when verification is weak; or when policy requires review. Critical work is at least T3. Other material T1–T2 work requires independent Sol/high review.
5. Inspect exposed agents. Use `default` for orchestration/synthesis, `explorer` for read-only discovery, and `worker` for bounded writes. Use custom agents only by visible configured name.
6. Select `current task | subagent | child task`. Use a subagent for bounded work returning immediately; use a child task for a durable independent outcome needing separate context, follow-up, approval, acceptance, or worktree. Multiple child tasks require a parent orchestrator.
7. Delegate only when independence, specialization, isolation, or review repays coordination. Parallelize read discovery; keep overlapping files, state, interfaces, or decisions under one writer. Material work gets an independent reviewer.
8. Record settings as **intended**, **configured**, **actual visible**, or **not verifiable**. Never infer hidden runtime facts.

## Issue route

For non-material T0–T1 work:

```text
Route: routed | compact | <T0/T1> | material: no | container: <current/subagent/child> | root/writer: <agent · model · reasoning> | discovery/reviewer: <assignment> | validation: <checks>
```

For T2–T5 or material work:

```md
## Execution route
Status / detail: routed | full
Intensity / materiality:
Container / dependency wave:
Parent / child role:
Thread / worktree requirement:
Source of truth / risk:
Root / discovery / writer / reviewer:
Validation:
Reviewed / model source:
```

Write into an authorized issue; otherwise return the block. Finish when every role, container, model, reasoning level, review, and validation assignment is explicit and execution has not started.
