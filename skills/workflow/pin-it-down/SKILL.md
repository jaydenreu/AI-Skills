---
name: pin-it-down
description: Resolve delivery-changing ambiguity and record durable decisions.
---

# Pin It Down

Interrogate a proposed delivery until execution no longer requires consequential guessing. Do not deliver the work.

Inspect available code, data, and documents before asking. Keep an ambiguity ledger:

`A1: <unknown> | delivery impact | recommended default | blocker/defaultable/deferrable`

Ask one highest-impact question at a time, recommend an answer, explain why it matters in one sentence, then wait. Update the ledger after every answer; challenge vague terms and scope expansion.

Cover only decisions that can change outcome, users, behavior, interfaces or data, permissions, failure states, constraints, ownership, risk, sequencing, non-goals, evidence, rollout, or review. For software, include schema/access, API/UI behavior, migration, and tests only when relevant.

Record durable choices in the agreed decision log as:

```md
### DEC-001 — <name>
Decision:
Requirement:
Evidence:
```

Finish only when blockers are resolved and remaining ambiguity is accepted as defaultable or deferrable. Return decision IDs, open items by status, and the next step—normally `write-the-brief`.
