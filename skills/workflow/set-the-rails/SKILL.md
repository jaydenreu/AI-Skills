---
name: set-the-rails
description: Establish a user-confirmed Rails Contract for how project work is managed.
---

# Set The Rails

Discover facts from the workspace; interview the user for policy. Existing artifacts are evidence, not authority unless explicitly designated. Do not deliver project work or silently invent governance.

Run a decision-complete interview: every coordination-changing choice must be confirmed, accepted as a default, or explicitly deferred. Track each as `R1: <choice> | impact | recommended default | blocker/defaultable/deferrable`.

## Interview

1. Locate the tracker, source of truth, decision and glossary locations, PRD location, standards, statuses, owners, review path, and completion evidence.
2. Separate observed facts from unresolved choices. Do not ask for discoverable facts or treat conventions as approved policy.
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
Statuses:
Standards:
Reviewers:
Done requires:
Evidence location:
Status: ready | <remaining gaps>
```

Finish only after the user confirms the contract or accepts its defaults, with no blocking gap in source of truth, decisions, PRD location, review, or done rules. Return the contract, changed locations, gaps by status, and `$pin-it-down` as the next skill when a concrete delivery exists.
