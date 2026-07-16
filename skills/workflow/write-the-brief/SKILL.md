---
name: write-the-brief
description: Publish resolved decisions as the project's canonical, execution-ready PRD.
---

# Write The PRD

Produce the canonical product requirements document (PRD) consumed by `$slice-the-work`. Read the Rails Contract for its location and use accepted decisions and project language. If a missing answer would change delivery, return to `$pin-it-down`; do not guess or reopen the interview here.

## Process

1. Define the users, problem, smallest valuable outcome, and explicit non-goals.
2. Trace accepted decisions into numbered, observable product requirements.
3. Capture behavior, failure states, permissions, affected interfaces, risks, and rollout only where relevant.
4. Define the strongest practical completion evidence and first vertical slice.
5. Publish the canonical PRD at the location defined by the Rails Contract.

```md
# PRD: <work>

## Users and problem
## Goal
## Non-goals
## Decisions
- DEC-001: <trace>
## Product requirements
- REQ-001: <observable requirement>
## Behavior and failure states
## Data, systems, and interfaces
## Risks and rollout
## Evidence
## First vertical slice
## Open blockers
```

Finish only when every accepted decision is traced, every requirement is observable or verifiable, and `$slice-the-work` can cover the PRD without guessing. Return the PRD location, blockers or material risks, and `$slice-the-work` as the next skill.
