---
name: set-the-rails
description: Configure a project or workspace so agents know the source of truth, decision log, tracker, standards, and done rules.
disable-model-invocation: true
---

# Set The Rails

Purpose: interview the workspace, not the work. Establish how delivery will be managed.

## Use when

- starting a new repo, project, team workflow, or workspace
- source of truth, tracker, decision log, or done rules are unclear
- moving this workflow into a new business, client, or org context

## Rules

- Do not deliver project work.
- Explore before deciding.
- Ask one setup section at a time.
- Reuse existing docs/tools. Do not create duplicates.
- Keep public docs generic. Keep employer/client-specific details private unless approved.

## Explore

Find the current rails:

- work tracker: GitHub, GitLab, Jira, Linear, local docs, spreadsheet, email, other
- source of truth: repo docs, Notion, Confluence, Drive, SharePoint, local docs, other
- decision log: decision docs, ADRs, tracker comments, meeting notes, other
- standards: coding, reporting, process, comms, governance, review rules
- statuses/labels: triage, blocked, ready, in progress, review, done
- owners/reviewers
- glossary/domain docs

## Decide

Lock in:

1. Where work lives.
2. Where durable decisions live.
3. Where glossary/domain language lives.
4. What statuses/labels mean.
5. What "done" requires.
6. Who reviews what.
7. Where completion evidence is recorded.

## Write

Create or update the smallest useful setup docs.

For repos, prefer:

- existing `AGENTS.md`, `CLAUDE.md`, or equivalent agent file
- `docs/agents/workflow.md`
- `docs/decisions/`
- `CONTEXT.md`

For non-code workspaces, use the agreed source of truth.

Do not create duplicate agent docs. Update the existing one if present.

Suggested repo note:

```md
## Agent workflow

Work tracker: <location>
Source of truth: <location>
Decision log: <location>
Glossary/domain docs: <location>
Standards: <location>
Done requires: <evidence/review/checks>
```

## Done

Return:

- work tracker
- source of truth
- decision log location
- glossary/domain location
- status/label meanings
- review/done rules
- changed files/docs
- recommended next command
