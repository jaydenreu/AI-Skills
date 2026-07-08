---
name: pin-it-down
description: Interview before delivery. Resolve ambiguity, challenge assumptions, and capture durable decisions.
disable-model-invocation: true
---

# Pin It Down

Purpose: make the work clear enough to execute without guessing.

## Preflight

Before interviewing, check whether these are clear:

- source of truth
- decision log
- output/tracker location
- done/review rules

If clear, continue.

If missing and the work is substantial, recommend `/set-the-rails` first. Do not run setup inside this skill unless asked.

## Rules

- Do not deliver the work.
- Be direct. Push until delivery-relevant ambiguity is gone.
- Keep an ambiguity ledger: blocker, defaultable, deferrable.
- Ask one question at a time.
- Recommend the answer before asking.
- Use existing docs/data/code before asking when possible.
- Challenge vague terms, hidden assumptions, weak defaults, and scope creep.
- Capture only durable decisions.
- Do not end while delivery blockers remain.

## Ambiguity Loop

Before the first question, inventory unresolved delivery decisions:

```md
A1: <unknown> | impact: <delivery impact> | default: <recommendation> | status: blocker/defaultable/deferrable
```

Ask in dependency order, starting with the blocker that unlocks the most downstream decisions. After each answer, record the decision, accepted default, or deferral, then update the ledger. Ask a narrowing follow-up when an answer stays broad: "simple", "polished", "soon", "better", "good", "reasonable", "done". Stop only when blockers are resolved and remaining ambiguity is defaulted or deferred.

## Cover

Work the decision tree in dependency order. Skip irrelevant areas.

- outcome
- users/stakeholders
- current state
- target state
- constraints
- data, systems, tools, or processes involved
- ownership and approvals
- permissions, controls, or governance
- edge cases, defaults, and failure states
- non-goals
- risks
- evidence of success
- rollout/order

For software, also cover:

- data/schema/RLS
- backend/services/APIs
- frontend/UI
- tests/checks

## Question format

Use this format:

```md
I recommend: <clear default>.
Why it matters: <one sentence>.
Question: <one direct question>.
```

Wait after each question.

## Capture

Use the agreed decision log.

For repos, prefer:

- `CONTEXT.md` for glossary terms only
- `docs/adr/` for hard-to-reverse architecture decisions
- `docs/decisions/<work>.md` for feature/project decisions

Decision format:

```md
### DEC-001 - <name>
Decision:
Requirement:
Evidence:
```

Keep entries short. Do not turn the decision log into a brief, PRD, backlog, or scratchpad.

## Done

Return:

- resolved decisions
- open decisions
- remaining ambiguity by blocker/defaultable/deferrable status
- decision IDs
- recommended next command, usually `/write-the-brief`
