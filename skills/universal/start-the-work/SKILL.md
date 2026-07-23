---
name: start-the-work
description: Route an unfamiliar or unconfigured repository into the right skill workflow and maintain its gated Work Path. Use when entering a repo, beginning substantial work, or choosing between universal and routed delivery.
---

# Start The Work

Own the Work Path, not specialist work.

## Route

1. Inspect the request and repository for a Rails Contract, context, decisions, PRD, issues, routes, tracker, and existing Work Path. Trust gates only with evidence.
2. Select:
   - **Routed delivery** for product or software delivery needing governance, traceable requirements, issues, review, and acceptance.
   - **Universal** for exploration, learning, operations, organization, or bounded work without delivery infrastructure.
   - **Universal → delivery** when discovery must precede a build decision.
3. Create or update:

```md
Route: universal | routed delivery | universal → delivery
| # | Skill | Gate / artifact | Status | Evidence |
```

Use `pending | current | complete | skipped`; justify every skip. Default delivery gates are `$set-the-rails` → `$pin-it-down` → `$write-the-brief` → `$slice-the-work` → `$model-route` → execution → integrated review → `$remember-the-work`. Use only the universal gates the outcome needs.

## Advance

Invoke exactly the current skill. After its gate passes, update and reassess the path. For multiple independent AFK outcomes, invoke `$model-route`, then `$orchestrate-the-work`; otherwise use `$deliver-the-slice` or `$carry-the-step`.

Keep the path in the current plan until `$set-the-rails` establishes its durable tracker. Finish with the chosen route, checked gates, evidence, and exactly one current skill.
