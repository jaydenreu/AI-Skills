---
name: pin-it-down
description: Run a decision-complete interview that resolves delivery-changing ambiguity.
---

# Pin It Down

Resolve a proposed delivery until execution no longer requires consequential guessing. Do not deliver the work or decide project rails here.

## Preflight

Inspect available code, data, and documents and read the Rails Contract. For substantial project work, if that contract is missing, conflicting, or stale, stop and recommend `$set-the-rails`; do not perform setup here.

## Interview

Keep an ambiguity ledger:

`A1: <unknown> | delivery impact | recommended default | blocker/defaultable/deferrable`

Ask the highest-impact question one at a time, recommend an answer, explain why it matters in one sentence, then wait. Update the ledger after every answer; challenge vague terms and scope expansion.

Cover only decisions that can change outcome, users, behavior, interfaces or data, permissions, failure states, constraints, ownership, risk, sequencing, non-goals, evidence, rollout, or review. For software, include schema/access, API/UI behavior, migration, and tests only when relevant.

Record durable choices in the agreed decision log as:

```md
### DEC-001 — <name>
Decision:
Requirement:
Evidence:
```

Finish only when every delivery-changing unknown is resolved, accepted as a default, or explicitly deferred. Return decision IDs, open items by status, and `$write-the-brief` as the next skill to publish the canonical PRD.
