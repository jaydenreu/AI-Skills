---
name: deliver-the-slice
description: Execute one routed issue, verify it, review it, and return completion evidence to its parent when delegated.
---

# Deliver The Slice

Deliver one issue without adjacent scope. Treat its brief, decisions, criteria, non-goals, execution route, and child contract as authoritative.

Before writing, confirm the route still matches scope and names the container, writer, review, and validation. Invoke `$model-route` only when missing, pending, stale, or invalidated.

## Process

1. Invoke `$remember-the-work` Recall with the issue's signals; state outcome, route, scope, evidence, and review.
2. If delegated, confirm parent, blockers, ownership, worktree, and return contract; report `started`.
3. Make the smallest end-to-end change. Keep overlapping files, state, interfaces, and decisions under one writer.
4. Verify with the strongest practical check; for software prefer a focused red → green → refactor loop through a public seam.
5. Check every criterion, then review separately for specification and standards. Material work requires the routed independent reviewer and revalidation.
6. If this task owns memory, invoke Capture; otherwise return candidates. Update the issue/tracker and parent:

```md
Status: completed | needs-attention
Outcome / criteria:
Changed surfaces:
Validation / review:
Route deviations:
Memory candidates or IDs:
Safe to accept: yes | no — rationale
Parent action:
```

If blocked, report the blocker and tightest reliable evidence; never imply an unrun check passed. Finish only after the parent return and completion reference are current.
