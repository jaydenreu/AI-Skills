# Model catalogue

**Last reviewed:** 2026-07-16

**Catalogue owner:** The organization overlay's `catalogue_owner`; otherwise the repository maintainer

**Fallback review cadence:** Reverify before every material current-fact recommendation and perform a full catalogue review at least every 90 days while the skill is in active use

**Scope:** Current OpenAI model, Codex surface, reasoning, subagent, and pricing facts used by `model-route`

This file is the detailed source of truth for volatile provider facts. At the maintainer's request, `../SKILL.md` deliberately mirrors the current GPT-5.6 names and task-intensity assignments so issues remain explicit. Update both files together. Organization and repository policy override this catalogue.

## Contents

- [Maintenance rule](#maintenance-rule)
- [Capability-class mapping](#capability-class-mapping)
- [Reasoning levels](#reasoning-levels)
- [Codex surfaces and agent threads](#codex-surfaces-and-agent-threads)
- [Current rates](#current-rates)
- [Organization overlay](#organization-overlay)
- [Known limitations](#known-limitations)
- [Update procedure](#update-procedure)
- [Official sources](#official-sources)

## Maintenance rule

Before a material recommendation about current models, prices, credits, or availability:

1. Check the last-reviewed date against the organization's review cadence, or the fallback cadence above when no overlay sets one.
2. Reverify any fact likely to have changed or consequential to the route.
3. Use only official provider documentation.
4. Mark unavailable or unexposed facts as unknown; never fill gaps from memory.

When a GPT-5.6 name, identifier, or task-intensity assignment changes, update this catalogue and the maintained model block in `../SKILL.md` together, then rerun the routing smoke cases. Rates, credits, surface availability, and detailed entitlements remain catalogue-only.

## Capability-class mapping

These are portable defaults, not entitlements or mandatory choices. Choose the cheapest organization-approved model that meets the class on the active surface.

| Capability class | Current mapping | Default reasoning | Use |
| --- | --- | --- | --- |
| **economy** | **Default issue route:** GPT-5.6 Luna, `gpt-5.6-luna`. **Optional cross-family cost override:** use GPT-5.4 mini for an exposed ChatGPT/Codex credit route or GPT-5.4 nano, `gpt-5.4-nano`, for credible simple high-volume API classification, extraction, ranking, and bounded subagent work when organization policy allows it. | Low/Light | Clear, repeatable, low-risk, high-volume work with exact verification. Issue routes stay on the maintained GPT-5.6 family unless an explicit approved override is recorded. |
| **balanced** | GPT-5.6 Terra, `gpt-5.6-terra` | Medium; High when measured need justifies it | Everyday bounded implementation, tool use, and read-heavy investigation. |
| **frontier** | GPT-5.6 Sol, `gpt-5.6-sol`; `gpt-5.6` is a verified alias to Sol | High or Extra High (`xhigh`) | Ambiguous, difficult, high-value, critical, architectural, synthesis, or review work. |
| **max** | GPT-5.6 Sol with Max reasoning | Max | One exceptional, tightly coupled, quality-first problem. This is a reasoning route, not a separate model slug. |
| **ultra** | Codex Ultra on an eligible account and supported selected model; current official selector documentation shows GPT-5.6 Sol | Ultra | Maximum reasoning with proactive subagent delegation for meaningful independent workstreams. This is a Codex mode, not an API model identifier. |

Other currently documented Codex choices include `gpt-5.4` and GPT-5.3-Codex-Spark (`gpt-5.3-codex-spark`). GPT-5.3-Codex-Spark is a text-only research preview for ChatGPT Pro users and was not available in the API at the review date.

The Codex models page marks `gpt-5.2` and `gpt-5.3-codex` deprecated for ChatGPT sign-in. API-key availability can differ; verify the API model catalogue before relying on a deprecated-for-Codex model.

## Reasoning levels

For GPT-5.6 through the Responses API, official guidance verifies:

`none`, `low`, `medium`, `high`, `xhigh`, `max`

The API defaults to `medium` when reasoning effort is omitted. The Codex interface uses human-facing labels such as Light, Medium, High, Extra High, and Max. Light corresponds to Low in the CLI; Extra High corresponds to `xhigh`.

GPT-5.4 nano and GPT-5.4 mini API reasoning support is `none` (their default), `low`, `medium`, `high`, and `xhigh`. Do not assign them Max or Ultra unless the current Codex surface explicitly exposes that supported mode.

Codex documentation also exposes Ultra on eligible accounts and supported models. Ultra combines maximum reasoning with automatic task delegation. Treat it separately from API `reasoning.effort`; the public GPT-5.6 API reasoning list stops at `max`.

Lower-latency values such as `minimal` or `none` are model-dependent in Codex configuration. Verify support on the selected model and surface before configuring them.

## Codex surfaces and agent threads

### Surface availability and control

| Surface | Verified routing facts at review date |
| --- | --- |
| ChatGPT Work on the web | Provides a composer model and intelligence control for available models. The GPT-5.6 family is the current recommended set; account and workspace eligibility still govern what appears. |
| ChatGPT desktop app, local task | Provides a model switcher and shared `config.toml` settings. Advanced controls expose specific models and reasoning where supported; Max or Ultra may need to be enabled in settings. |
| Codex CLI | Supports `/model` interactively and `--model`/`-m` for launch or `codex exec`; use verified identifiers from this catalogue only when the authenticated account or API key exposes them. |
| Codex IDE extension | Uses the shared local configuration and exposes model/reasoning selection; subagent UI depends on background-agent availability. |
| Codex cloud task | Uses a service-selected default; the user could not change that default model at the review date. Do not promise a configured model for cloud execution. |
| API-key local/SDK use | Model access follows the models available to the API key and uses API token pricing. ChatGPT credit rates, account-only Ultra behavior, and cloud integrations do not automatically apply. |

Verified current behavior:

- ChatGPT Work can run subagent workflows for eligible accounts. At most intelligence levels, request delegation explicitly; Ultra can delegate proactively.
- ChatGPT Work's web sidebar reports subagent activity and completed details but does not provide individual stop or steer controls; ask ChatGPT to manage those threads.
- Current local Codex releases support explicit subagent requests in the ChatGPT desktop app, Codex CLI, and IDE extension. Applicable `AGENTS.md` or skill instructions can also request delegation.
- The desktop app exposes each subagent thread. The CLI exposes agent threads through `/agent`. The IDE extension exposes them through the background-agent interface when available.
- Local custom model selection and reasoning configuration apply through the shared `config.toml` used by the desktop app, CLI, and IDE extension. The default model for Codex cloud tasks was not user-selectable at the review date.
- `agents.max_threads` defaults to 6 when unset. It is a cap on concurrent open agent threads, not a target.
- `agents.max_depth` defaults to 1: the root can spawn direct children, but those children cannot spawn deeper descendants by default.
- Subagents inherit the parent sandbox policy. Live parent permission and sandbox overrides are reapplied when children spawn; an individual custom-agent file may provide defaults, but live parent choices still matter.
- Subagent workflows consume more tokens than comparable single-agent runs because each worker performs its own model and tool work.

### Custom agents and repository guidance

`AGENTS.md` contains repository-specific operating rules and closer files take precedence for their subtree. `model-route` contains reusable routing logic; it does not replace repository guidance.

Local Codex custom agents are standalone TOML files under `~/.codex/agents/` for personal agents or `.codex/agents/` for project agents. Current required fields are `name`, `description`, and `developer_instructions`. Optional settings can include `model`, `model_reasoning_effort`, `sandbox_mode`, `mcp_servers`, and `skills.config`; other supported normal configuration keys can layer approval or permission behavior. Omitted values inherit from the parent session. Use configured named agents where they are visible and suitable. Otherwise use logical roles and disclose the fallback.

Current documentation lists built-in `default`, `worker`, and `explorer` agents. A custom agent with the same name takes precedence. Do not assume any additional specialist agent exists.

| Agent type/name | Default routing use |
| --- | --- |
| `default` | Root orchestration and synthesis; general-purpose fallback; independent review only in a fresh read-only child thread. |
| `explorer` | Read-heavy discovery, impact analysis, repository search, evidence gathering, and dependency mapping. |
| `worker` | Bounded implementation, fixes, transformations, and test execution. |
| Configured custom agent | Use by its exact exposed name only when its documented specialty matches the work; never invent one. |

The root composer or configuration determines the root route. A custom-agent file may pin a child route. Neither proves the runtime route actually used unless the interface or execution record exposes it.

## Current rates

### ChatGPT Codex credits

Credits per 1 million tokens, from the official Codex pricing rate card:

| Model | Input | Cached input | Output |
| --- | ---: | ---: | ---: |
| GPT-5.6 Sol | 125 | 12.5 | 750 |
| GPT-5.6 Terra | 62.5 | 6.25 | 375 |
| GPT-5.6 Luna | 25 | 2.5 | 150 |
| GPT-5.5 | 125 | 12.5 | 750 |
| GPT-5.4 | 62.5 | 6.25 | 375 |
| GPT-5.4 mini | 18.75 | 1.875 | 113 |

The rate card did not publish a token credit rate for GPT-5.3-Codex-Spark at the review date. Official pricing says GPT-5.6 usage averages 5-40 credits per message, but individual messages can vary materially.

### API token prices

USD per 1 million text tokens for the current API models used by this catalogue:

| Model identifier | Input | Cached input | Output |
| --- | ---: | ---: | ---: |
| `gpt-5.4-nano` | $0.20 | $0.02 | $1.25 |
| `gpt-5.4-mini` | $0.75 | $0.075 | $4.50 |
| `gpt-5.6-sol` | $5.00 | $0.50 | $30.00 |
| `gpt-5.6-terra` | $2.50 | $0.25 | $15.00 |
| `gpt-5.6-luna` | $1.00 | $0.10 | $6.00 |

For the GPT-5.6 family, prompts above 272K input tokens are priced at 2x input and 1.5x output for the full request, and explicit cache writes are billed at 1.25x the uncached input rate. Verify these rules before a cost-sensitive large-context route.

API token rates and ChatGPT credit rates are different billing systems. Do not convert between them without an official conversion rule.

Actual usage depends on uncached input, cached input, output, hidden reasoning, tool activity, the number of agent threads, duplicated context, retries, testing, validation, and review. No official fixed Max or Ultra cost multiplier was found. Report measured usage when available and bounded uncertainty otherwise.

## Organization overlay

Copy and fill this block in an organization-owned policy location. Do not store sensitive policy or credentials in the generic skill.

```yaml
organization_model_route:
  policy_owner: ""
  catalogue_owner: ""
  review_cadence: ""
  approved_models: []
  approved_ai_surfaces: []
  permitted_data_classifications: []
  browsing_rules: ""
  connector_rules: ""
  sandbox_requirements: ""
  permission_requirements: ""
  maximum_thread_count: null
  maximum_nesting_depth: 1
  cost_or_credit_limits: ""
  mandatory_human_review_categories: []
  mandatory_independent_agent_review_categories: []
  prohibited_uses: []
  escalation_route: ""
```

Organization policy overrides the generic catalogue, and repository policy overrides generic routing recommendations within its scope. This overlay does not replace security, legal, privacy, governance, procurement, or human-accountability requirements.

## Known limitations

- Plans, workspace admin settings, staged rollouts, geography, authentication method, and surface can change model and Ultra availability.
- Public documentation cannot reveal the actual root or child model used in a specific run. Verify it from visible configuration or runtime records when available.
- Ultra's worker-model choices and internal routing are not publicly exposed; do not infer them.
- The active environment can set a lower thread cap or different nesting depth than the documented defaults.
- Cloud task model selection was fixed at the review date and may change later.
- Custom-agent configuration is documented as evolving; recheck the schema before generating organization-wide agent files.
- The organization overlay above is intentionally unset until an organization owner fills and approves it.

## Update procedure

1. Verify current official provider documentation.
2. Update the catalogue's last-reviewed date.
3. Update model mappings, identifiers, reasoning support, surface availability, and rates; mirror GPT-5.6 names and task-intensity assignments into `../SKILL.md`.
4. Run the routing smoke cases in [orchestration-patterns.md](orchestration-patterns.md).
5. Inspect recommendations that changed and confirm they still follow lowest-cost-credible routing.
6. Record material policy changes in the repository's decision or change record, when one exists.

## Official sources

- [Codex models](https://learn.chatgpt.com/docs/models)
- [Codex pricing and credits](https://learn.chatgpt.com/docs/pricing)
- [Codex subagents and custom agents](https://learn.chatgpt.com/docs/agent-configuration/subagents)
- [Build skills](https://learn.chatgpt.com/docs/build-skills)
- [GPT-5.6 model guidance and reasoning support](https://developers.openai.com/api/docs/guides/latest-model)
- [GPT-5.4 nano model, reasoning support, and API pricing](https://developers.openai.com/api/docs/models/gpt-5.4-nano)
- [GPT-5.4 mini model, reasoning support, and API pricing](https://developers.openai.com/api/docs/models/gpt-5.4-mini)
- [GPT-5.6 Sol model and API pricing](https://developers.openai.com/api/docs/models/gpt-5.6-sol)
- [GPT-5.6 Terra model and API pricing](https://developers.openai.com/api/docs/models/gpt-5.6-terra)
- [GPT-5.6 Luna model and API pricing](https://developers.openai.com/api/docs/models/gpt-5.6-luna)
