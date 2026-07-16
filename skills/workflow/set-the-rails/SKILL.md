---
name: set-the-rails
description: Establish a user-confirmed Rails Contract, including AI routing policy.
---

# Set The Rails

Discover workspace facts; interview the user for policy. Treat artifacts as evidence, not authority unless designated. Do not deliver work or invent governance.

Run a decision-complete interview: confirm, default, or defer every coordination-changing choice. Track each as `R1: <choice> | impact | recommended default | blocker/defaultable/deferrable`.

## Interview

1. Locate the tracker, source of truth, decisions/glossary, PRD location, AI routing policy, standards, statuses, owners, review path, and completion evidence.
2. Separate facts from choices. Do not ask for discoverable facts or treat conventions as policy.
3. Ask the highest-impact unresolved choice one at a time, then wait:

```md
Found: <evidence or none>
Recommend: <default>
Why: <coordination impact>
Question: <one choice>
```

4. Update the ledger after each answer. Before writing, ask the user to confirm the assembled contract.
5. Update the smallest existing workflow or agent document; avoid duplicates and unapproved private details.

## Rails Contract

```md
Tracker:
Source of truth:
Decisions / glossary:
PRD location:
AI routing policy: <location | none; use $model-route defaults>
Statuses:
Standards:
Reviewers:
Done requires:
Evidence location:
Status: ready | <remaining gaps>
```

Finish only after the user confirms the contract or accepts its defaults, with no blocking gap in source of truth, decisions, PRD location, AI routing policy, review, or done rules. Return the contract, changed locations, gaps by status, and `$pin-it-down` as the next skill when a concrete delivery exists.
