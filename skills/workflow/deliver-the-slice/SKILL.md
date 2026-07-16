---
name: deliver-the-slice
description: Deliver one routed slice without scope drift, using its explicit model and agent route, evidence, checks, review, and a clear completion record.
---

# Deliver The Slice

Purpose: complete one vertical slice safely.

## Rules

- Work on one slice only.
- Do not expand into adjacent work.
- Use the agreed source of truth.
- Verify outcomes, not internal activity.
- Prefer simple interfaces and fewer handoffs.
- Avoid pass-through abstractions and process theatre.
- Finish with evidence and review.
- Read and honor the issue's `Execution route` before changing anything.
- If the route is missing, pending, materially stale, or inconsistent with the slice, invoke `$model-route Recommend` and update the issue before execution.

## Process

1. Read the slice, parent brief, decisions, acceptance criteria, non-goals, and `Execution route`.
2. Confirm the route names the intensity, materiality, root, discovery, writer, reviewer, GPT-5.6 model, reasoning, parallelism, and validation. Refresh it with `$model-route Recommend` when required.
3. Inspect current state and relevant docs/data/code/systems.
4. State a short plan:
   - outcome to prove
   - evidence/checks
   - likely files/docs/systems/processes touched
   - review path
   - intended agent/model/reasoning route
5. Deliver vertically:
   - create or run the smallest failing/absent check where practical
   - make the smallest useful change
   - run the focused check
   - refine while still passing
   - repeat
6. Run relevant checks:
   - focused tests/reports/reconciliations
   - typecheck/lint for code
   - data validation for analytics
   - process/control checks for ops
   - sign-off/review where required
7. Verify every acceptance criterion.
8. Review separately:
   - Spec: matches brief/slice and avoids scope creep
   - Standards: follows project rules, language, and conventions
9. Complete `Delivery routing outcome` in the issue with actual visible agent/model/reasoning facts, unknowns, deviations, review, corrections, validation, and acceptance safety.
10. Record completion in the tracker/source of truth.

## Software loop

For code changes, prefer:

```md
RED: write/run one failing test or check.
GREEN: implement the smallest fix.
CHECK: pass the focused check.
REFACTOR: improve while green.
RECHECK: run the check again.
```

Test behaviour, not internals. Use the highest useful public seam. Mock only external boundaries.

## If evidence is blocked

State why, then use the tightest reliable check available. Do not skip verification silently.

## Done

Return:

- delivered outcome
- decision/criteria coverage
- evidence/checks and results
- review result
- intended route, actual visible route, and deviations
- agents/threads used and model/reasoning facts that were visible
- completion reference: commit, issue, doc, report, approval, or tracker update
- true follow-up work only
