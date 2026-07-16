# Orchestration patterns

Read this only for delegated execution or route auditing. The routing decision and model map stay in `../SKILL.md`.

## Workstream contracts

Before spawning, define one bounded contract per child:

```text
WORKSTREAM PLAN
ID / objective / independence rationale:
Agent / model / reasoning:
Read or write / writable scope / permissions:
Source of truth / inputs / dependencies:
Non-goals:
Expected result / validation:
Parallel-with / completion wave:
```

Require:

```text
WORKSTREAM RESULT
ID / status: complete | partial | blocked
Actual visible agent/model/reasoning:
Confirmed findings and evidence:
Changes / validation:
Assumptions / unresolved risks / next action:
```

Reject an unbounded objective, missing source of truth, unclear write scope, or result that cannot be accepted independently.

## Independence and writer gates

A stream is parallel-ready only when its inputs are available, it needs no frequent cross-stream decisions, it returns an independently reviewable result, and it can be paused or discarded safely. Read streams must not write. Concurrent writers need disjoint files/state **and** disjoint semantics, with an explicit integration owner.

Use one writer whenever files, database objects, interfaces, definitions, architecture, migrations, configuration precedence, or policy overlap. Similar labels do not prove independence.

## Dependency waves

1. **Discover:** run useful independent read-only mapping or audits.
2. **Synthesize:** wait for every required result, reconcile contradictions, resolve blockers, and select one approach.
3. **Write:** use one writer for coupled work; parallel writers only for truly isolated scopes.
4. **Validate/review:** test the integrated result. Material work gets a fresh independent read-only reviewer; return findings to the writer and revalidate corrections.

The root owns boundaries, permissions, synthesis, acceptance, and the final report. A concurrency limit is a cap, not a target; use the fewest useful children and default to one nesting level unless repository policy says otherwise.

## Route and execute

Print the intended route before work. Preserve one source of truth, stop on unresolved consequential semantics, wait for dependency waves, and record the actual visible route, deviations, changed artifacts, checks, review findings, corrections, residual uncertainty, and acceptance safety.

## Audit

Compare intended, configured, actual visible, and unverifiable routing facts; agents used; duplicated work; validation/review; rework; outcome quality; residual risk; and available cost, token, credit, or latency evidence. State whether a cheaper credible route could likely have produced the same accepted result and why. Do not infer hidden models or reasoning from output quality.
