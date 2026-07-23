---
name: set-the-rails
description: Establish a user-confirmed Rails Contract, including AI routing and thread policy.
---

# Set The Rails

Discover workspace facts; interview the user for policy. Treat artifacts as evidence, not authority. Do not deliver work or invent governance.

Track every coordination-changing choice as `R1: <choice> | impact | recommended default | blocker/defaultable/deferrable`.

## Interview

1. Locate the tracker, source of truth, Work Path, decisions/glossary, PRD, AI routing, thread authority, concurrency, worktrees, reporting, integration, standards, statuses, owners, review, and completion evidence.
2. Separate facts from choices. Do not ask for discoverable facts or treat convention as policy.
3. Ask the highest-impact unresolved choice one at a time:

```md
Found: <evidence or none>
Recommend: <default>
Why: <coordination impact>
Question: <one choice>
```

4. Update the ledger after each answer. Ask the user to confirm the assembled contract before writing.
5. Update the smallest existing workflow or agent document; avoid duplicates and unapproved private details.

## Rails Contract

```md
Tracker / source of truth:
Work Path:
Decisions / glossary:
PRD location:
AI routing policy: <location | $model-route defaults>
Thread authority: recommend | automatic within accepted plan | never
Maximum concurrent child tasks:
Parallel writes require worktrees:
Child status reporting:
Integration owner:
Statuses / standards:
Reviewers:
Done requires / evidence location:
Status: ready | <gaps>
```

Finish after user confirmation with no blocking gap in source, decisions, routing, thread authority, review, or done rules. Return the contract, changed locations, gaps, and `$pin-it-down` when concrete delivery exists.
