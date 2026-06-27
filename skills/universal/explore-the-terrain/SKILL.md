---
name: explore-the-terrain
description: Explore an uncertain topic, idea, opportunity, problem, domain, market, story world, game concept, learning area, dataset, tool, or personal direction before committing to a plan. Use when the user wants to research, compare possibilities, generate options, understand tradeoffs, or dive into ideas without prematurely narrowing the work.
---

# Explore The Terrain

Purpose: turn uncertainty into a useful map of possibilities, constraints, and next probes.

## Rules

- Do not force a delivery plan too early.
- Separate facts, interpretations, options, assumptions, and preferences.
- Use the best available sources or artifacts for the domain.
- Mark confidence clearly.
- Prefer small probes over grand conclusions.
- Record reusable maps, experiment logs, and decisions as durable artifacts.
- End with a recommended next move.

## Process

1. Frame the exploration question.
2. Inventory what is already known, available, and assumed.
3. Choose useful lenses:
   - software: users, architecture, constraints, tools, risks
   - analytics: definitions, data availability, validity, decisions, audience
   - creative: theme, form, references, voice, audience, constraints
   - learning: target ability, prerequisites, feedback, practice environment
   - personal: energy, values, friction, defaults, support, cadence
4. Inspect or research enough evidence to avoid pure speculation.
5. Map promising paths, dead ends, open questions, and cheap experiments.
6. Decide what, if anything, should be saved as a durable artifact or versioned note.
7. Recommend the next probe, decision, brief, or step.

## Output

Use this shape:

```md
# Terrain: <topic>

## Question
<what we are trying to understand>

## Known
- <facts or existing context>

## Paths
- <option>: <promise, tradeoff, confidence>

## Frictions
- <risk, missing context, dependency, or uncertainty>

## Probes
- <small experiment, read, sketch, query, prototype, conversation, practice attempt>

## Artifact / Record
<what to save, commit, log, or leave as scratch>

## Recommendation
<next move and why>
```

## Done

Return:

- the terrain map
- confidence level
- durable map, experiment log, or scratch decision
- recommended next move
- whether to continue with `clarify-the-aim`, `shape-the-brief`, or `carve-the-path`