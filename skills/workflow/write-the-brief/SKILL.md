---
name: write-the-brief
description: Turn resolved context into a concise delivery brief. No interview unless a blocker is missing.
disable-model-invocation: true
---

# Write The Brief

Purpose: convert decisions into an execution-ready brief.

## Rules

- Do not re-interview unless a blocker would change delivery.
- Use current context, docs, decisions, data, code, and prior work.
- Use project language from the glossary/source of truth.
- Preserve decision IDs.
- Separate goals from non-goals.
- Be concise. No filler.

## Process

1. Identify scope.
2. Read enough context to avoid fiction.
3. Map decisions to required outcomes and behaviour.
4. Identify the best evidence seam: test, report, demo, metric, approval, audit trail, or review.
5. Write the brief.
6. Publish to the agreed tracker/source of truth.

## Format

```md
# Brief: <work>

## Problem
<problem being solved>

## Goal
<smallest valuable outcome>

## Non-goals
- <excluded work>

## Decisions
- DEC-001: <short trace>

## Outcome
<what will be true when done>

## Behaviour / Process
<observable behaviour, workflow, defaults, permissions, handoffs, empty/error/success states>

## Data, systems, and interfaces
<tables, APIs, reports, tools, docs, teams, processes, or integrations affected>

## Evidence
<tests, checks, demo, metric, sign-off, report, approval, or audit trail>

## First delivery slice
<smallest end-to-end slice worth delivering>

## Open questions
Only blockers that can change delivery.
```

## Done

Return:

- brief reference/location
- key risks or blockers
- recommended next command, usually `/slice-the-work <ref>`
