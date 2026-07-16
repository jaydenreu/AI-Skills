---
name: slice-the-work
description: Break a brief or plan into small vertical slices that each produce a verifiable outcome and carry an explicit model and agent execution route.
---

# Slice The Work

Purpose: turn a brief into agent-ready delivery slices.

## Rules

- Slice by outcome, not by function, team, layer, or activity type.
- Each slice must produce something visible or verifiable.
- Preserve decision IDs.
- Keep slices small enough to deliver and review.
- Mark human input clearly.
- Avoid isolated setup tickets unless they unblock multiple slices.
- Put an `Execution route` in every published issue or slice.
- Use `$model-route Recommend` after the slice is defined; do not guess the model, agent, or reasoning assignment.

## Vertical slicing

For software, each slice may cut through:

- data/schema/permissions
- backend/services/APIs
- frontend/UI
- tests/checks

For business, ops, analytics, or process work, each slice may cut through:

- process/workflow
- data/reporting
- systems/tools
- controls/approvals
- comms/training
- evidence/review

Do not create separate schema/API/UI/process/reporting tickets unless they are true prefactor or unblocker work.

## Process

1. Read the brief fully.
2. Extract decisions, outcomes, constraints, non-goals, and evidence.
3. Inspect enough context to sequence work sensibly.
4. Draft slices in dependency order.
5. Mark each slice:
   - `AFK`: agent can proceed without more input
   - `HITL`: human decision/review required
6. Ask for granularity approval unless told to proceed.
7. Invoke `$model-route Recommend` for each accepted slice and attach its issue execution-route block:
   - compact for non-material T0-T1;
   - full manifest for T2-T5 or material work.
8. Publish the routed slices to the agreed tracker/source of truth.

## Slice format

```md
# <slice title>

Type: AFK | HITL
Parent:
Blocked by:

## Outcome
What works or is true when this is done.

## Covers
- DEC-001

## Build / Change
End-to-end change to deliver.

Workstreams touched:
- Data/reporting:
- Systems/tools:
- Process/workflow:
- Interface/UI/comms:
- Controls/review:
- Evidence:

## Acceptance criteria
- [ ] Outcome is visible or verifiable
- [ ] Main empty/error/failure path is handled
- [ ] Required control, permission, or review rule is covered
- [ ] Evidence proves the slice

## Out of scope
What this slice must not expand into.

## Execution route

Routing status: routed | pending
Routing detail: compact | full
Intensity: T0 | T1 | T2 | T3 | T4 | T5
Material: yes | no — rationale
Route reviewed: YYYY-MM-DD
Model source reviewed: YYYY-MM-DD
Root: <agent | GPT-5.6 model | reasoning>
Discovery: <none or assignments>
Writer: <agent | model | reasoning>
Reviewer: <none or independent assignment>
Parallelism: <none or dependency-aware streams>
Validation: <required evidence>
Routing manifest: <compact line or full manifest>
```

## Done

Return:

- ordered slices
- dependencies
- AFK/HITL status
- decision coverage
- routing status, intensity, and compact/full manifest
- created refs, if published

Do not rewrite the parent brief except by linking slices.
