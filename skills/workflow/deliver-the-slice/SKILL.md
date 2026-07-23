---
name: deliver-the-slice
description: Execute one routed issue, verify it, review it, and record completion.
---

# Deliver The Slice

Deliver one issue without adjacent scope. Treat its brief, decisions, acceptance criteria, non-goals, and `Execution route` as authoritative.

Before writing, confirm the route still matches scope and materiality and names the model/reasoning, agents, review, and validation. Invoke `$model-route Recommend` only when it is missing, pending, stale enough to matter, or invalidated by changed requirements.

## Process

1. Invoke `$remember-the-work` Recall with the issue's signals; state the outcome, intended route, write scope, evidence, and review plan.
2. Make the smallest end-to-end change. Keep overlapping work under one writer and follow the routed dependency waves.
3. Verify with the strongest practical check; for software, prefer a focused red → green → refactor loop and test behavior through a public seam.
4. Check every acceptance criterion, then review separately for specification and project standards. Material work requires the routed independent reviewer and revalidation after corrections.
5. Invoke `$remember-the-work` Capture when material, then update the issue and tracker with completion evidence and routing outcome:

```md
Actual visible route:
Deviations / unknowns:
Review and corrections:
Validation result:
Memory: none — <reason> | recalled <IDs> | updated <IDs>
Safe to accept: yes | no — rationale
```

If evidence is blocked, report the blocker and tightest reliable proxy; never imply unrun checks passed. Finish with the outcome, criteria coverage, evidence, review result, route deviations, completion reference, and true follow-up only.
