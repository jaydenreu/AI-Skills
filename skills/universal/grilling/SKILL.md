---
name: grilling
description: Interview relentlessly about a plan or design. Use when the user wants to stress-test a plan before building, sharpen a design, expose hidden assumptions, or uses any grill trigger phrase.
---

# Grilling

Purpose: stress-test a plan until blockers are resolved and remaining ambiguity is explicit.

## Rules

- Do not build the plan.
- Use code, docs, data, or artifacts before asking when possible.
- Ask one question at a time and wait.
- Recommend an answer with each question.
- Keep an ambiguity ledger: blocker, defaultable, deferrable.
- Challenge vague terms, hidden assumptions, weak defaults, scope creep, and unowned risks.
- Do not finish while blockers remain.

## Ambiguity Loop

Before the first question, inventory unclear decisions:

```md
A1: <unknown> | impact: <why it matters> | default: <recommendation> | status: blocker/defaultable/deferrable
```

Ask in dependency order, starting with the blocker that unlocks the most downstream decisions. After each answer, record the decision, default, or deferral, then update the ledger. Ask a narrowing follow-up when an answer stays broad: "simple", "polished", "soon", "better", "good", "reasonable", "done". Stop only when blockers are resolved and remaining ambiguity is defaulted or deferred.

## Cover

Walk only relevant branches:

- goal, audience, current state, target state
- constraints, risks, permissions, non-goals
- core design choices and rejected alternatives
- systems, tools, data, people, or materials
- edge cases, defaults, failure states
- evidence, sequencing, ownership, review path

For software, cover data/schema, backend/API, frontend/UI, tests/checks, migration, observability, and rollback when relevant.

## Question Format

```md
I recommend: <clear default>.
Why it matters: <one sentence>.
Question: <one direct question>.
```

## Done

Return resolved decisions, remaining ambiguity by status, accepted defaults, risks, and next step.