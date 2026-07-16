# Orchestration patterns

Use this reference when `model-route` delegates work, needs reusable route examples, or evaluates routing behavior. The stable policy and routing manifest remain in `../SKILL.md`; current model facts and the organization overlay remain in `model-catalog.md`.

## Contents

- [Workstream plan contract](#workstream-plan-contract)
- [Workstream result contract](#workstream-result-contract)
- [Issue execution-route contract](#issue-execution-route-contract)
- [Independence gate](#independence-gate)
- [Task-intensity route examples](#task-intensity-route-examples)
- [Execution-wave patterns](#execution-wave-patterns)
- [Invocation examples](#invocation-examples)
- [Static smoke-test cases](#static-smoke-test-cases)

## Workstream plan contract

Complete this contract before spawning a worker. One contract describes one bounded workstream.

```text
WORKSTREAM PLAN

Workstream ID:
Objective:
Why it is independent:
Agent type/name:
Agent role:
Capability class:
Resolved model:
Reasoning effort:
Read or write:
Permission/approval boundaries:
Writable paths:
Permitted scope:
Non-goals:
Required inputs:
Source of truth:
Dependencies:
Expected output:
Validation:
Can run in parallel with:
Must complete before:
```

Reject vague objectives such as "investigate everything," "fix the system," "improve the codebase," or "review all issues." A valid objective has a bounded question or artifact, a permitted scope, a source of truth, and a result the root can accept or reject.

Example read-only audit stream:

```text
WORKSTREAM PLAN

Workstream ID: SECURITY-01
Objective: Identify authentication and authorization regressions in the accepted diff.
Why it is independent: It reads the integrated diff and tests but makes no implementation decisions or writes.
Agent type/name: `default` in a fresh read-only child; use configured `security-reviewer` if available
Agent role: Independent reviewer
Capability class: frontier
Resolved model: Current frontier mapping from `model-catalog.md`
Reasoning effort: high
Read or write: Read-only
Permission/approval boundaries: No state changes, external messages, or approval requests
Writable paths: None
Permitted scope: Changed authentication code, authorization policy, and related tests
Non-goals: Implementation, style-only review, or changes outside the accepted diff
Required inputs: Accepted brief, integrated diff, repository security guidance
Source of truth: AGENTS.md, authorization policy, accepted tests
Dependencies: Integrated writer output
Expected output: Prioritized material findings with file and line evidence
Validation: Every finding maps to an invariant or acceptance criterion
Can run in parallel with: DATA-REVIEW-01, TEST-REVIEW-01
Must complete before: Final acceptance
```

## Workstream result contract

Require every worker to return:

```text
WORKSTREAM RESULT

Workstream ID:
Status:
Actual agent type/name:
Actual model/reasoning visible:
Confirmed findings:
Evidence:
Changes made, if permitted:
Validation performed:
Assumptions:
Unresolved questions:
Risks:
Recommended next action:
```

`Status` should be one of `complete`, `partial`, or `blocked`. Confirmed findings must be separated from hypotheses. A worker that changed files must list them explicitly and stay inside its permitted scope.

## Issue execution-route contract

Put this block in every issue or delivery slice. A non-material T0-T1 issue may use a compact one-line manifest; T2-T5 and all material issues require the full manifest from `../SKILL.md`.

```md
## Execution route

Routing status: routed | pending
Routing detail: compact | full
Intensity: T0 | T1 | T2 | T3 | T4 | T5
Material: yes | no — rationale
Route reviewed: YYYY-MM-DD
Model source reviewed: YYYY-MM-DD

Root: <agent type/name> | <GPT-5.6 model> | <reasoning>
Discovery: <none or agent/model/reasoning assignments>
Writer: <root, worker, or configured custom agent> | <model> | <reasoning>
Reviewer: <none or independent agent/model/reasoning>
Parallelism: <none or dependency-aware workstreams>
Validation: <tests, checks, reconciliation, review>

Routing manifest: <compact line or full manifest>

### Delivery routing outcome

Actual visible route: <verified facts and unknowns>
Route deviations: <none or explanation>
Review and corrections: <results>
Validation result: <results>
Safe to accept: yes | no — rationale
```

`slice-the-work` creates and populates the initial block through `$model-route Recommend`. `deliver-the-slice` consumes it and completes `Delivery routing outcome`. Preserve intended versus actual visible facts; do not rewrite an unavailable runtime model as if it were verified.

## Independence gate

Treat a stream as parallel-ready only when all required conditions hold:

- Its objective can complete without frequent decisions from another stream.
- Its source of truth and required inputs are available before it starts.
- It returns an independently reviewable result or artifact.
- It does not make a shared metric, business, product, analytical, or architectural decision.
- A read stream has no writes.
- A write stream has a path and semantic scope disjoint from every concurrent writer.
- It is safe to pause, retry, or discard without corrupting shared state.
- The root has an integration owner and a planned synthesis or integration gate.

If a required condition fails, keep the work sequential or redefine the boundary. Similar labels do not prove independence; shared files, invariants, definitions, and decisions disprove it.

### One-writer gate

Use one writer when any of these overlap:

- files or database objects;
- business, product, metric, or analytical definitions;
- architectural direction or public interface;
- migrations, backfills, or ordering-sensitive state;
- configuration with shared precedence;
- documentation that states the same policy or source of truth.

Allow parallel writers only when their scopes and semantics are disjoint, isolation is real, and integration ownership is explicit. Prefer separate worktrees for code changes and separate artifacts for non-code work. The root integrates; workers do not merge competing decisions.

## Task-intensity route examples

Use these as concrete defaults; resolve capability classes to current models through `model-catalog.md`.

```text
T0 Exact
Root: default | gpt-5.6-luna | low
Children: none
Writer: root
Reviewer: none; use deterministic validation
```

```text
T1 Routine
Root: default | gpt-5.6-terra | medium
Discovery: explorer | gpt-5.6-terra | low/medium, only if context is missing
Writer: worker | gpt-5.6-terra | medium
Reviewer: separate default | gpt-5.6-sol | high, only when material
```

```text
T2 Demanding
Root: default | gpt-5.6-terra | high
Discovery: explorer | gpt-5.6-terra | medium
Writer: worker | gpt-5.6-terra | high
Reviewer: configured specialist or separate default | gpt-5.6-sol | high, when material
```

```text
T3 Critical
Root: default | gpt-5.6-sol | high
Discovery: explorer | gpt-5.6-terra/medium for inventory; gpt-5.6-sol/high for consequential judgment
Writer: worker or configured specialist | gpt-5.6-sol | xhigh
Reviewer: configured domain reviewer or separate default | gpt-5.6-sol | high
```

```text
T4 Exceptional coupled
Root and sole writer: default | gpt-5.6-sol | Max
Discovery: optional targeted explorer | gpt-5.6-terra | medium
Reviewer: separate default or configured specialist | gpt-5.6-sol | high/xhigh
Parallel implementation: no
```

```text
T5 Broad independent
Root orchestrator: default | gpt-5.6-sol | high, or Ultra after the Ultra gate
Read streams: explorer | gpt-5.6-luna/low for exact extraction, gpt-5.6-terra/medium by default, gpt-5.6-sol/high for consequential judgment
Write streams: one worker per disjoint scope | each routed at T1-T3
Integrated reviewer: configured specialist or separate default | gpt-5.6-sol | high
```

## Execution-wave patterns

### Pattern A: four independent audit dimensions

Wave 1 can run security, data integrity, test coverage, and usability audits as four read-only direct children. Give each a separate invariant set and result contract. Wait for all four. At synthesis, deduplicate shared findings, resolve contradictory severity judgments, and produce one prioritized recommendation.

Do not ask any audit worker to repair the result. If repair is authorized, choose one writer after synthesis.

### Pattern B: coupled implementation that only appears parallel

A database change, API behavior, client behavior, and documentation may look like four streams. Keep them under one writer when they share one semantic decision or acceptance path. Parallelize only read-only impact analysis before writing and independent validation after integration.

The safe sequence is:

```text
parallel impact analysis -> synthesis and accepted design -> one writer -> integrated validation -> independent review -> correction -> revalidation
```

### Pattern C: isolated parallel implementations

Parallel implementation is credible when two accepted slices touch separate packages or artifacts, share no source-of-truth decision, and have explicit integration tests. Assign separate worktrees or artifacts, make each worker validate its slice, then let the root integrate and run the combined checks. An independent reviewer assesses the integrated result, not just each isolated branch.

### Pattern D: critical writer and reviewer correction loop

Use a frontier critical writer for sensitive logic. After the writer validates, give the integrated artifact to an independent read-only reviewer. Return material findings to the same writer, rerun affected tests and reconciliation, and ask the reviewer to verify material fixes. Record both the original finding and correction evidence in the routing outcome.

### Pattern E: no subagents

For a tiny exact change, state that coordination would cost more than execution. Use direct root execution or one economy worker only if switching is genuinely cheaper and visible. Run the exact check and report that no agent thread was needed.

## Invocation examples

### Recommendation only

```text
$model-route Recommend the model, reasoning effort, and agent/thread route for this task. Do not execute it.
```

Require the response to name the exact built-in or configured custom agent, capability/resolved model, and reasoning level for the root, every child, the writer, and the reviewer.

### Route an issue

```text
$model-route Recommend and write the execution route into this issue. Use a compact route for non-material T0-T1 work or the full manifest for T2-T5/material work. Include the route date and GPT-5.6 model-source review date. Do not execute the issue.
```

### Bounded execution

```text
$model-route Route and execute this bounded change. Use one writer and proportionate validation.
```

### Parallel investigation

```text
$model-route Act as the orchestrator. Divide this investigation into genuinely independent read-only workstreams, spawn one thread per useful workstream, run them in parallel, wait for every required result, reconcile contradictions, and return one evidence-backed recommendation.
```

### Parallel implementation with safeguards

```text
$model-route Determine whether these implementation slices are genuinely independent. Parallelize only disjoint write scopes, use separate worktrees where appropriate, keep overlapping edits under one writer, then integrate, test, and independently review the combined result.
```

### Critical change

```text
$model-route Treat this as critical work. Identify the source of truth and invariants, use a frontier route for consequential reasoning, keep one writer, and require independent review.
```

### Audit

```text
$model-route Audit the intended and actual route for this completed task. Assess quality, validation, rework, thread usage, residual risk, and whether a cheaper credible route could have produced the same accepted outcome.
```

### Composition with existing skills

```text
$model-route Use the repository's existing general workflow to frame the task, then arrange the model, thread, execution-wave, and review route.
```

```text
First use the relevant general skills to orient, explore, shape, and carve the work. Then use $model-route to select models, agents, dependencies, parallel workstreams, and review.
```

```text
$model-route Audit whether the model and agent route used during execution was proportionate to the risk and accepted outcome.
```

## Static smoke-test cases

Evaluate these without launching paid nested tasks. For each case, produce the route, then compare it with the expected invariants. A case passes only when every expected invariant is present and no prohibited behavior appears.

### Case 1: tiny mechanical task

**Scenario:** Rename one settled heading in a fixed file and verify the exact text.

**Expected:** The issue contains a compact routed block dated against the model source; `Material: no`; root/`default` on `gpt-5.6-luna` at low; no child; root writer; no reviewer beyond exact comparison or diff check.

### Case 2: normal bounded implementation

**Scenario:** Add a specified endpoint following an existing pattern with known acceptance tests.

**Expected:** The issue contains a compact routed block; T1; `default` root and one `worker` writer on `gpt-5.6-terra` at medium; proportionate tests; an explicit materiality assessment. This scenario is normally `Material: no` when it is local, reversible, and strongly covered by the known tests; use a separate `gpt-5.6-sol`/high `default` reviewer only when a materiality gate or repository policy applies.

### Case 3: ambiguous high-risk logic

**Scenario:** Change a governed financial metric whose definitions conflict across sources.

**Expected:** The issue contains a full routing manifest; T3 and `Material: yes`; `default` root on `gpt-5.6-sol`/high; one `worker` or custom specialist on Sol/xhigh; explicit source-of-truth and invariants; unresolved semantics stop execution; a matching custom reviewer or separate read-only `default` on Sol/high reviews after implementation.

### Case 4: one tightly coupled difficult problem

**Scenario:** Resolve a rare cross-system consistency failure that needs one coherent causal model.

**Expected:** The issue contains a full routing manifest; T4 and `Material: yes` because shared cross-system behavior is affected; root/`default` is the sole writer on `gpt-5.6-sol`/Max; no artificial fan-out; targeted validation; a separate `default` or matching custom reviewer on Sol/high or xhigh.

### Case 5: four independent audit dimensions

**Scenario:** Review an integrated change separately for security, data integrity, test gaps, and accessibility.

**Expected:** The issue contains a full routing manifest; T5; `default` root on `gpt-5.6-sol`/high; four `explorer` read-only streams on `gpt-5.6-terra`/medium if concurrency and value justify them; wait for every result; reconcile and synthesize; no writer.

### Case 6: apparently parallel but coupled implementation

**Scenario:** Database, API, UI, and documentation edits all depend on one new business definition.

**Expected:** The issue contains a full routing manifest; detect shared semantics and likely shared files; `default` root owns synthesis; keep implementation under one sequential `worker` routed on Terra or Sol at the resulting T2 or T3 intensity; allow `explorer` discovery and independent review in parallel; no competing definitions.

### Case 7: parallel isolated implementations

**Scenario:** Two accepted slices affect separate packages and have no shared interfaces or decisions.

**Expected:** The issue contains a full routing manifest; T5; `default` root on `gpt-5.6-sol`/high; one `worker` per disjoint scope with its own Luna/Terra/Sol T1-T3 route and separate worktree or artifact where appropriate; explicit integration owner; combined tests; separate Sol/high `default` or custom review of the integrated output.

### Case 8: stale model catalogue

**Scenario:** The recommendation depends on today's prices, but the catalogue exceeds the organization's or fallback review cadence.

**Expected:** Inspect the last-reviewed date; verify material facts from official provider sources; update or qualify the catalogue; never present stale rates or availability as current.

### Case 9: runtime does not expose the actual model

**Scenario:** A completed task shows its prompts and agent threads but not model identities.

**Expected:** Separate intended and visible route; state that actual models and reasoning are not verifiable; never infer them from output quality.

### Case 10: existing skill overlap

**Scenario:** A repository already has a skill that owns most routing and orchestration decisions.

**Expected:** Inspect and reuse, improve, or merge the existing owner; do not create a competing workflow; preserve one source of truth for each routing decision.
