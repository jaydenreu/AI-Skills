---
name: model-route
description: Select and orchestrate the lowest-cost credible model, reasoning effort, and concrete agent/thread route for a task or issue. Use only when explicitly invoked with $model-route for issue/slice routing, task-intensity routing, named agent assignments, recommendation, route-and-execute, route auditing, delegation, parallel workstreams, writer/reviewer splits, or model-cost decisions. Do not use for ordinary low-risk requests that are not being published as issues and need no routing decision.
---

# Model Route

Use the lowest-cost route that is credible for the risk, then escalate when evidence shows that route is inadequate. Treat capability as a fit decision, not a prestige ladder.

Read [references/model-catalog.md](references/model-catalog.md) before naming current models, reasoning levels, availability, prices, or credits, or applying an organization overlay. If its review date is stale enough to affect the decision, verify the material facts from its official sources before routing. Read [references/orchestration-patterns.md](references/orchestration-patterns.md) before delegating, producing workstream contracts, or evaluating the smoke cases.

## Current GPT-5.6 model set

**Reviewed:** 2026-07-16

This skill intentionally lists the current GPT-5.6 models directly so issue routes remain explicit. The maintainer accepts that this block is static and must be updated when OpenAI changes the lineup.

| Model | Identifier | Use in this skill |
| --- | --- | --- |
| **GPT-5.6 Luna** | `gpt-5.6-luna` | T0 exact, clear, repeatable, high-volume, lowest-cost GPT-5.6 work |
| **GPT-5.6 Terra** | `gpt-5.6-terra` | T1 routine and T2 demanding everyday implementation, exploration, and tool use |
| **GPT-5.6 Sol** | `gpt-5.6-sol`; `gpt-5.6` is the Sol alias | T3 critical, T4 exceptional coupled, T5 orchestration, synthesis, and independent review |

Use Low/Light for quick well-scoped work, Medium for ordinary planning, High or Extra High (`xhigh`) for difficult multi-step or critical work, Max for one hardest coupled problem, and Ultra only for a broad route with meaningful independent subagent work. Organization policy and actual surface availability still override this default.

When maintaining this static mapping, update this section, the task-intensity table below, [references/model-catalog.md](references/model-catalog.md), and the issue-routing examples together. Verify against [OpenAI's Codex models page](https://learn.chatgpt.com/docs/models) and [GPT-5.6 model guidance](https://developers.openai.com/api/docs/guides/latest-model).

## Respect ownership and policy

Apply rules in this order:

1. Law, security, privacy, legal, and governance requirements.
2. Organization policy and approved AI surfaces.
3. Applicable `AGENTS.md`, repository configuration, and repository standards.
4. The accepted brief, decisions, source of truth, and human instructions.
5. This generic routing guidance and the model catalogue.

Repository and organization policy override generic recommendations. A model choice never replaces deterministic calculations, tests, reconciliation, validation, independent review, human accountability, security controls, or production safeguards.

Compose with existing skills instead of replacing them:

| Decision | Owner |
| --- | --- |
| Outcome, source of truth, constraints, risk, done rules | Orientation or rails skills |
| Missing evidence and ambiguity | Clarification or exploration skills |
| Accepted solution and brief | Shaping or brief skills |
| Outcome-based steps, slices, and dependencies | Carving or slicing skills |
| Model, reasoning, logical roles, threads, waves, and independent review | `model-route` |
| Implementation, checks, and completion record | Execution or delivery skills |
| Learning for future routes | Repository retrospective or practice process, when one exists |

Treat a workstream plan as an execution overlay over accepted steps or slices, not as a competing backlog. Do not invoke `model-route` recursively.

If the active repository already has an authoritative model-routing or orchestration owner, reuse or improve that owner instead of creating a competing workflow. Record which source owns each overlapping decision.

## Select one mode

- **Recommend**: Classify the task, print the route, explain it, and stop before doing the underlying work.
- **Route and execute**: Classify, print the route, coordinate the work, validate it, arrange proportionate review, and report the visible route actually used.
- **Audit**: Compare an intended or completed route with visible configuration, execution evidence, outcome quality, usage, and residual risk. Do not execute or redo the underlying task unless separately asked.

Infer the mode from the request. Default to Recommend when the user asks only what should be used. Never treat a recommendation as authorization to execute.

## Route issues and slices

Treat the issue or slice as the execution source of truth when one is provided.

1. Read the issue, parent brief, decisions, dependencies, acceptance criteria, non-goals, and existing route.
2. Classify and route it before execution.
3. Use a compact route for non-material T0-T1 work. Use the full routing manifest for T2-T5 or any material work.
4. Write the `Execution route` block from [references/orchestration-patterns.md](references/orchestration-patterns.md) into the issue when tracker mutation is authorized. Otherwise return the exact block for the caller to publish.
5. Record the route date, model-source review date, exact root/discovery/writer/reviewer assignments, resolved GPT-5.6 model, reasoning, parallelism, and validation.
6. In Recommend mode, stop after routing the issue. In Route and execute mode, preserve the intended route and append the actual visible route, deviations, review, and validation after delivery.

Do not leave an issue merely marked "routing required." Either attach the compact/full route or mark it `pending` with the exact blocker. Re-run routing when requirements, materiality, model availability, or the maintained model date changes materially.

## Classify the task

Choose exactly one primary class. Record risk separately so an independent-workstreams classification never hides critical work.

| Class | Use when |
| --- | --- |
| **Mechanical** | The target is exact, repetitive, local, and cheaply verified: renames, formatting, approved-schema fixtures, fixed-file inventories, or settled edits. |
| **Bounded** | Requirements, acceptance criteria, and affected scope are understood, and normal tests or review can verify the result: a defined endpoint, settled pipeline or SQL step, specified component, pattern-following refactor, or document with an agreed structure. |
| **Critical** | Plausible-looking work could be subtly wrong or have material blast radius: ambiguous semantics, governed metrics, finance, sensitive data, security, privacy, access control, tenancy, migrations, backfills, historical reinterpretation, critical operations, high-impact architecture, weak testability, or conflicting truth. |
| **Exceptional coupled problem** | One unusually difficult problem spans tightly coupled systems and needs a sustained, coherent mental model. Size or file count alone is insufficient. |
| **Independent workstreams** | Several bounded pieces can proceed concurrently, produce separate evidence, and later be synthesized. Record each stream's risk and dependencies. |

## Assess the routing factors

Evaluate all of these before choosing a route:

- **Outcome**: the artifact, implementation, decision, or evidence required.
- **Source of truth**: authoritative files, data, definitions, specifications, policies, systems, or humans.
- **Ambiguity**: execution against settled requirements versus discovery and consequential choice.
- **Risk**: financial, security, privacy, legal, regulatory, metric-governance, availability, integrity, user, reversibility, and reputational impact.
- **Context breadth**: one local area, one subsystem, or several cross-cutting systems.
- **Verifiability**: strength and cost of tests, reconciliation, exact comparison, deterministic checks, or independent review.
- **Coupling**: whether workstreams can finish independently or require one shared mental model.
- **Cost and latency**: whether delegation improves elapsed value or quality enough to repay coordination and duplicated context.
- **Failure history**: failed tests, missed invariants, contradictions, repeated rework, unexplained uncertainty, or incomplete results from a cheaper route.

Resolve source-of-truth gaps through the owning workflow before consequential execution. Ask a human only when the missing choice materially changes the route or outcome and cannot be discovered safely.

## Decide materiality

Record a binary materiality decision before execution. Mark `Material: yes` when any of these gates applies:

- the task is **Critical**;
- a plausible failure affects shared or production behavior, multiple users or downstream consumers, security, privacy, access, finance, governed metrics, compliance, availability, or data integrity;
- the change is destructive, irreversible, difficult or expensive to roll back, or includes a migration, backfill, historical reinterpretation, or authoritative decision;
- the work changes a shared interface, source of truth, policy, architecture, or definition used beyond one isolated scope;
- verification is weak, nondeterministic, unavailable, or depends substantially on expert judgment; or
- repository or organization policy requires material handling or independent review.

Otherwise mark `Material: no`. Mechanical work is normally non-material. Bounded work always needs an explicit assessment; local, reversible work with strong deterministic checks is normally non-material. Treat an exceptional coupled problem as material unless the manifest demonstrates that every gate above is absent. For independent workstreams, assess the integrated outcome rather than lowering materiality because its pieces are separate. If consequential uncertainty prevents a defensible decision, classify the work as Critical and resolve it before execution.

## Choose an explicit agent and reasoning route

Use stable capability classes in manifests and resolve them to current models through the catalogue. Every route must name the agent type or configured custom-agent name, capability class, resolved model when selectable, and reasoning effort for the root and every child. If the runtime does not expose or permit a setting, label it `intended` rather than omitting it.

| Capability class | Meaning |
| --- | --- |
| **economy** | Lowest-cost approved capability credible for exact, low-risk, cheaply verified work. |
| **balanced** | General-purpose capability for normal bounded implementation and read-heavy investigation. |
| **frontier** | Strong capability for ambiguity, consequential decisions, architecture, synthesis, critical logic, and independent review. |
| **max** | Deepest supported single-agent reasoning for an exceptional tightly coupled problem. |
| **ultra** | Maximum reasoning plus proactive parallel delegation on a supported surface. |

### Resolve concrete agent types

Use the current built-in Codex agents by name:

- **`default`**: root orchestration, consequential synthesis, a general-purpose fallback, or an independent review in a fresh read-only thread.
- **`explorer`**: read-only repository, document, dependency, log, lineage, impact, or evidence discovery.
- **`worker`**: bounded implementation, fixes, mechanical transformations, and test execution.

First inspect the agent types exposed by the active environment. Use a configured custom agent by its exact name when its documented specialty matches the work; for example, prefer an available `security-reviewer` for a security review. Never invent a custom agent or assume it is installed. If no custom reviewer exists, use `default` in a fresh read-only child thread. If subagents are unavailable, keep the route sequential under the root and disclose the fallback.

### Route by task intensity

Apply this table as the default. Resolve each capability class to the active model through the catalogue.

| Intensity | Work | Root route | Discovery route | Writer route | Reviewer route | Delegation |
| --- | --- | --- | --- | --- | --- | --- |
| **T0 Exact** | Mechanical, local, deterministic | Root/`default`; `gpt-5.6-luna`; low/Light | None | Root; or one `worker` on Luna/low only for a real batch | None beyond exact checks | No child by default |
| **T1 Routine** | Normal bounded work with settled acceptance | `default`; `gpt-5.6-terra`; medium | Optional `explorer`; Terra; low or medium | One `worker`; Terra; medium | If material, fresh read-only `default`; `gpt-5.6-sol`; high | At most one useful child at a time |
| **T2 Demanding** | Bounded but cross-file, multi-step, or context-heavy | `default`; `gpt-5.6-terra`; high | `explorer`; Terra; medium | One `worker`; Terra; high | If material, custom reviewer or fresh read-only `default`; `gpt-5.6-sol`; high | Parallel read-only discovery allowed; one writer |
| **T3 Critical** | Security, privacy, finance, governed data, migrations, access, ambiguous high-impact logic | `default`; `gpt-5.6-sol`; high | `explorer`; Terra/medium for inventory, Sol/high when its judgment is consequential | One `worker` or matching custom specialist; Sol; xhigh/Extra High | Matching custom reviewer, else fresh read-only `default`; Sol; high | Parallel read-only audits allowed; exactly one writer |
| **T4 Exceptional coupled** | One unusually hard, tightly coupled problem needing one coherent model | Root/`default`; `gpt-5.6-sol`; Max | Optional targeted `explorer`; Terra; medium | Root is the sole writer; Sol; Max | Fresh read-only `default` or matching custom reviewer; Sol; high or xhigh | No parallel implementation |
| **T5 Broad independent** | Several genuinely independent workstreams with a synthesis gate | `default`; `gpt-5.6-sol`; high, or Ultra only after its gate | One `explorer` per useful read stream; Luna/low for exact extraction, Terra/medium by default, Sol/high for consequential judgment | One `worker` per disjoint write scope, each routed at T1-T3 | Matching custom reviewer or fresh read-only `default`; Sol; high on integrated output | Fewest direct children that cover the independent work |

For T5, assign every child its own T0-T3 intensity; do not give all children the root's expensive route. Critical classification always implies at least T3. Materiality controls mandatory independent review, not whether the agent and reasoning route must be explicit.

Use `none` or `minimal` only for T0 when the selected model supports it and exact validation makes reasoning unnecessary. Use medium for ordinary planning, high for multi-step reasoning and review, xhigh for critical implementation or unusually difficult analysis, Max only for T4, and Ultra only for a justified T5 route. Escalate one dimension at a time from evidence.

## Keep the root accountable

The root thread remains the orchestrator. It owns classification, source-of-truth identification, routing assumptions and blocker questions, workstream boundaries, capability and reasoning assignments, dependencies, permissions, write scopes, spawning, steering, waiting, synthesis, conflict resolution, validation, independent review, and acceptance. Delegation does not transfer accountability.

Keep the root focused on requirements, decisions, constraints, accepted evidence, synthesis, and final output. Isolate noisy searches, logs, exploratory dead ends, and large test output in bounded workers when that isolation is worth its cost.

## Decide whether to delegate

State why delegation is or is not worthwhile.

Delegate when independent work can materially reduce elapsed time, specialization improves quality, a cheaper worker can safely perform a bounded task, noisy exploration should be isolated, independent review is required, alternatives need isolated comparison, or a batch divides naturally into independent items.

Do not delegate when the task is tiny, the worker prompt approaches the size of the task, streams need constant coordination, workers would edit the same files or logic, source of truth is unresolved, coordination costs exceed the likely benefit, or parallelism would create competing architectural, analytical, metric, product, or business decisions.

Before spawning, use the exact `WORKSTREAM PLAN` contract in [references/orchestration-patterns.md](references/orchestration-patterns.md). Make every worker return its `WORKSTREAM RESULT` contract and distinguish confirmed facts from hypotheses.

Prefer direct child threads. Keep the default maximum nesting depth at one unless a documented workflow justifies deeper nesting. Treat a concurrency limit as a cap, not a target; use the fewest threads that cover the independent work. Wait for every required result in a dependency wave.

## Emit the routing manifest

Before material execution, print the full manifest:

```text
ROUTING MANIFEST

Mode:
Issue or slice:
Task class:
Material: yes/no — rationale
Routing detail: compact/full
Route reviewed:
Model source reviewed:
Outcome:
Source of truth:
Risk:
Root or orchestrator:
Root agent type/name:
Root capability class and resolved model:
Root reasoning:
Workstreams:
  ID | agent type/name | role | scope | capability/model | reasoning | read/write | wave
Delegation decision:
Parallel execution:
Writer agent type/name:
Reviewer agent type/name:
Capability route:
Reasoning route:
Why this route:
Validation:
Escalation triggers:
Runtime facts not verifiable:
```

For each workstream include the exact built-in or configured custom-agent name, role, bounded scope, read/write status, dependency wave, intended capability class, resolved model when selectable, reasoning effort, and why it can or cannot run in parallel. For non-material trivial work, print a compact one-line route that still records mode, task class, `Material: no`, `agent=root/default`, capability/model, reasoning, delegation, and validation.

Label facts as **intended**, **configured**, **actual visible**, or **not verifiable**. Never claim the root model, reasoning level, child model, agent identity, or runtime setting unless the active interface, configuration, or execution record exposes it.

In Recommend mode, stop after the manifest and explanation.

## Execute in dependency-aware waves

### Wave 1: independent discovery

Parallelize useful read-heavy repository exploration, lineage, logs, official-document verification, dependency mapping, test-gap analysis, impact analysis, research, and independent option analysis.

At the synthesis gate, wait for every required result, compare evidence, reconcile contradictions, identify gaps, update the plan, decide whether implementation remains justified, and select one accepted approach. Synthesis is a decision, not concatenation.

### Wave 2: controlled implementation

Use one primary writer for overlapping code, SQL, data logic, governed definitions, configuration, documentation, architecture, and product decisions. Give the writer bounded scope, acceptance criteria, non-goals, source of truth, and relevant tests.

Allow parallel writing only when scopes are genuinely disjoint, dependencies are explicit, separate worktrees or artifacts isolate changes where appropriate, no shared semantic or architectural decision is being made independently, integration ownership is clear, and an integration-and-validation step is planned. Keep overlapping writes sequential.

### Wave 3: validation and independent review

Parallelize independent test execution, security review, correctness review, data-quality validation, documentation review, performance review, accessibility review, or acceptance-criteria comparison when useful. For material work, the final reviewer must be independent of the writer.

Return material findings to the writer. After correction, rerun affected validation, have the reviewer verify material fixes when required, inspect the integrated diff or final artifact, and only then accept the result.

## Gate Max and Ultra

Use **Max** for one exceptional, tightly coupled problem when one coherent mental model matters, several plausible approaches need deep comparison, high or extra-high reasoning has proved inadequate, delegation would damage coherence, and the blast radius justifies deeper sustained reasoning. Max is not the default for all important work.

Before recommending **Ultra**, explain:

1. The genuinely independent workstreams.
2. Why parallel completion materially improves speed or quality.
3. Why explicit focused workers under a non-Ultra lead are insufficient.
4. The expected additional usage or uncertainty about it.
5. How overlapping writes will be prevented.
6. How results will be waited for and synthesized.

Do not use Ultra for an ordinary feature, bounded bug fix, standard analysis, normal document, defined migration, or task with one primary execution path. Explicit parallel subagents can be used without Ultra when the environment supports them. Do not publish a fixed Max or Ultra cost multiplier unless current official documentation provides one.

## Audit a route

Compare:

- intended route;
- configured route;
- actual visible route;
- models and reasoning levels that can be verified;
- threads or agents used;
- duplicated effort and coordination overhead;
- validation evidence and independent review;
- rework and correction loops;
- accepted outcome quality;
- residual risk;
- available cost, token, credit, latency, or usage signals.

Identify whether a cheaper credible route could likely have produced the same accepted outcome, and state the evidence for that inference. Treat hidden runtime routing, internal reasoning, unexposed worker models, and unavailable usage details as unknown.

## Escalate from evidence

Escalate capability, reasoning, review, or isolation when the current route produces failed tests, missed invariants, contradictory findings, repeated rework, unexplained uncertainty, unresolved high-impact semantics, inadequate context handling, or an incomplete result. Change the smallest routing dimension that addresses the evidence; do not jump automatically to the most expensive route.

If named agents, model controls, or subagent threads are unavailable, use the closest safe sequential route and disclose the limitation. If the requested model or reasoning setting is unavailable, apply repository and organization policy, choose the cheapest available credible substitute, and mark the substitution as configured or intended rather than actual unless verified.

## Report the routing outcome

For material Route and execute work, finish with:

```text
ROUTING OUTCOME

Intended route:
Actual visible route:
Material: yes/no — rationale
Issue or slice updated:
Threads or agents used:
Agent/model/reasoning assignments:
Parallel workstreams completed:
Writer:
Reviewer:
Files or artifacts changed:
Validation performed:
Review findings:
Corrections made:
Unresolved uncertainty:
Escalations:
Cost or usage observations:
Safe to accept:
```

Judge success by the accepted outcome, correctness, evidence, validation, rework, elapsed value, usage efficiency, and residual risk. Do not judge success by model prestige or agent count.

## Completion criteria

Complete Recommend only after the route is classified, proportionate, explained, and explicitly non-executing. Complete Audit only after intended, configured, visible, and unknown facts are separated and residual risk is stated. Complete Route and execute only after every required wave has reported, contradictions are synthesized, overlapping work has one writer, material work has independent review, corrections are revalidated, and the visible route and remaining uncertainty are reported. For issue-backed work, completion also requires the compact/full route or delivery routing outcome to be written into the issue when mutation is authorized, or returned as an exact publishable block otherwise.
