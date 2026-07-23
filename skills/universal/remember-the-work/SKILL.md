---
name: remember-the-work
description: Maintain repository memory for decisions, failed approaches, incidents, and reusable guardrails. Use before revisiting an issue and after work produces a consequential decision, failure, or lesson.
---

# Remember The Work

Maintain project memory, not a transcript. Never store chain-of-thought, secrets, routine actions, or raw logs when an evidence link suffices.

## Locate

Honor `AGENTS.md` or the project contract. Otherwise use `docs/project-memory/INDEX.md` and `docs/project-memory/records/`, created lazily. Keep decision logs and ADRs canonical; link rather than duplicate.

## Recall

Before a new hypothesis or consequential decision:

1. Search the index, then records, by exact error, symptom, domain term, component/path, and issue or decision ID.
2. Verify status and applicability against current code, configuration, and evidence.
3. Report matching IDs, guardrails, conflicts, and staleness. A verified no-match is valid.

## Capture

Capture results that could prevent a future costly choice, failure, or diagnosis. Update the closest record; otherwise assign the next `PM-NNNN` and add one index row. In orchestrated work, children return candidates; the parent writes after reconciliation.

```md
# PM-NNNN — <title>
Date: <YYYY-MM-DD>
Status: active | superseded by <ID>
Kind: decision | incident | failed-attempt | learning
Scope / signals: <search terms>
Finding / decision: <outcome-level rationale>
Evidence: <tests, paths, commits, issues, logs>
Attempts: <failures worth avoiding and why>
Guardrail / trigger: <future action>
Links: <canonical and related IDs>
```

Finish with `Memory: none — <reason> | recalled <IDs> | updated <IDs>`. Require evidence, no duplicated canonical decision, and no sensitive reasoning.
