---
name: carve-the-path
description: Break a brief, goal, curriculum, creative ambition, analysis, product, workspace change, or personal project into small ordered steps that each create visible progress and evidence. Use when work is too large, vague, or tangled to execute in one pass.
---

# Carve The Path

Purpose: turn a goal into a sequence of verifiable steps.

## Rules

- Slice by outcome, not by activity type, tool, layer, or mood.
- Each step must produce something visible, testable, usable, felt, or reviewable.
- Prefer release-sized steps: each creates a durable artifact, learning proof, or record-worthy state.
- Preserve decisions and non-goals.
- Mark human input clearly.
- Keep steps small enough to finish and inspect.
- Avoid isolated setup unless it unlocks multiple later steps.

## Process

1. Read the brief, goal, notes, decisions, constraints, and evidence.
2. Identify the smallest meaningful proof of progress.
3. Draft steps in dependency order.
4. Mark which steps are commit-worthy, log-worthy, publish-worthy, or intentionally scratch.
5. Label each step:
   - `AFK`: an agent can proceed without more user input
   - `HITL`: human decision, material, review, or lived action required
6. Check coverage against outcome, evidence, risks, and non-goals.
7. Publish or return the path.

## Step Format

```md
# <step title>

Type: AFK | HITL
Parent:
Blocked by:

## Outcome
What works, exists, is learned, is decided, or becomes easier.

## Change
The end-to-end step to perform.

## Touches
- Materials:
- Tools or spaces:
- People or feedback:
- Evidence:
- Version / record:

## Acceptance Criteria
- [ ] Outcome is visible or verifiable
- [ ] Main failure, empty, awkward, or confusion path is handled
- [ ] Evidence proves the step
- [ ] Non-goals are respected

## Out of Scope
What this step must not expand into.
```

## Domain Notes

For software, a step may cross data, backend, frontend, tests, docs, and deployment.

For analytics, a step may cross source data, definitions, query/report, validation, and audience review.

For creative work, a step may cross reference, outline, draft, revision, and feedback.

For learning, a step may cross lesson, exercise, feedback, repetition, reflection, and a practice log.

For workspace or personal systems, a step may cross sorting, placement, defaults, routine, reset, and a completion record.

## Done

Return:

- ordered steps
- AFK/HITL status
- dependencies
- evidence coverage
- commit-worthy, log-worthy, or scratch steps
- recommended first step