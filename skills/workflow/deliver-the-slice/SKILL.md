---
name: deliver-the-slice
description: Deliver one slice without scope drift, using evidence, checks, review, and a clear completion record.
disable-model-invocation: true
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

## Process

1. Read the slice, parent brief, decisions, acceptance criteria, and non-goals.
2. Inspect current state and relevant docs/data/code/systems.
3. State a short plan:
   - outcome to prove
   - evidence/checks
   - likely files/docs/systems/processes touched
   - review path
4. Deliver vertically:
   - create or run the smallest failing/absent check where practical
   - make the smallest useful change
   - run the focused check
   - refine while still passing
   - repeat
5. Run relevant checks:
   - focused tests/reports/reconciliations
   - typecheck/lint for code
   - data validation for analytics
   - process/control checks for ops
   - sign-off/review where required
6. Verify every acceptance criterion.
7. Review separately:
   - Spec: matches brief/slice and avoids scope creep
   - Standards: follows project rules, language, and conventions
8. Record completion in the tracker/source of truth.

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
- completion reference: commit, issue, doc, report, approval, or tracker update
- true follow-up work only
