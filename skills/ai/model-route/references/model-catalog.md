# Model catalogue

**Last reviewed:** 2026-07-16
**Fallback cadence:** Reverify material current facts and review this file at least every 90 days while active.

The maintained GPT-5.6 routing map lives in `../SKILL.md`. Read this catalogue only for volatile availability, reasoning, surface, pricing, credit, or organization-policy facts. Use official sources; mark unexposed facts unknown.

## Reasoning and surfaces

GPT-5.6 API reasoning: `none`, `low`, `medium`, `high`, `xhigh`, `max`; default `medium`. Codex labels Low as Light and `xhigh` as Extra High. Ultra is an eligible Codex mode with proactive delegation, not an API model identifier. Verify lower settings and availability on the selected model and surface.

| Surface | Routing constraint |
| --- | --- |
| ChatGPT Work/web | Model/intelligence controls depend on account and workspace eligibility. |
| Desktop, CLI, IDE | Shared local configuration can expose model/reasoning and subagents. |
| Codex cloud | Do not promise a selectable model unless the current surface exposes it. |
| API key | Access and token pricing follow the key, not ChatGPT credits. |

Current built-ins are `default`, `explorer`, and `worker`; custom agents must be visibly configured. Subagents inherit parent safety policy, add context/usage cost, and may be constrained by active thread/depth limits. Visible configuration does not prove the runtime model actually used.

## Current rates

ChatGPT Codex credits per 1M tokens:

| Model | Input | Cached | Output |
| --- | ---: | ---: | ---: |
| GPT-5.6 Sol | 125 | 12.5 | 750 |
| GPT-5.6 Terra | 62.5 | 6.25 | 375 |
| GPT-5.6 Luna | 25 | 2.5 | 150 |
| GPT-5.5 | 125 | 12.5 | 750 |
| GPT-5.4 | 62.5 | 6.25 | 375 |
| GPT-5.4 mini | 18.75 | 1.875 | 113 |

API USD per 1M text tokens:

| Model | Input | Cached | Output |
| --- | ---: | ---: | ---: |
| `gpt-5.4-nano` | $0.20 | $0.02 | $1.25 |
| `gpt-5.4-mini` | $0.75 | $0.075 | $4.50 |
| `gpt-5.6-sol` | $5.00 | $0.50 | $30.00 |
| `gpt-5.6-terra` | $2.50 | $0.25 | $15.00 |
| `gpt-5.6-luna` | $1.00 | $0.10 | $6.00 |

Prompts above 272K GPT-5.6 input tokens cost 2× input and 1.5× output for the request; explicit cache writes cost 1.25× uncached input. Verify before a cost-sensitive route. Credits and API dollars are different systems; do not convert without an official rule. No official fixed Max/Ultra multiplier is known.

## Organization overlay

Store approved models/surfaces, data classifications, browsing/connectors, sandbox/permission rules, thread/depth limits, cost limits, mandatory human/independent review, prohibited uses, owners, cadence, and escalation route in an organization-controlled policy. Never put credentials or sensitive policy in this generic skill. Organization and repository policy override this catalogue.

## Maintenance

1. Verify official sources and update the review date.
2. Update volatile facts here; update GPT-5.6 names and T0–T5 assignments in `../SKILL.md` when they change.
3. Run [routing-evals.md](routing-evals.md) and inspect changed recommendations.
4. Record material policy changes in the repository decision log when one exists.

## Official sources

- [Codex models](https://learn.chatgpt.com/docs/models)
- [Codex pricing](https://learn.chatgpt.com/docs/pricing)
- [Subagents and custom agents](https://learn.chatgpt.com/docs/agent-configuration/subagents)
- [GPT-5.6 guidance](https://developers.openai.com/api/docs/guides/latest-model)
- [GPT-5.4 nano](https://developers.openai.com/api/docs/models/gpt-5.4-nano)
- [GPT-5.4 mini](https://developers.openai.com/api/docs/models/gpt-5.4-mini)
- [GPT-5.6 Sol](https://developers.openai.com/api/docs/models/gpt-5.6-sol)
- [GPT-5.6 Terra](https://developers.openai.com/api/docs/models/gpt-5.6-terra)
- [GPT-5.6 Luna](https://developers.openai.com/api/docs/models/gpt-5.6-luna)
