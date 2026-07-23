---
name: orchestrate-the-work
description: Coordinate independent work through Codex child tasks and dependency waves while the parent remains orchestrator. Use for parallel or separately followable outcomes needing status, isolation, integration, and return to a parent.
---

# Orchestrate The Work

After branching, keep the parent as control plane; do not implement there.

1. Read the accepted Work Path, slices, dependencies, Rails thread policy, and relevant memory. Invoke `$model-route` for the topology; stop on unresolved consequential decisions.
2. Choose `current task | subagent | child task`. Use child tasks for durable independent outcomes needing separate context, follow-up, acceptance, approval, or a worktree. Honor `recommend | automatic within accepted plan | never`.
3. Before creating child tasks, read [thread-contracts.md](references/thread-contracts.md). Invoke `$model-route` for every child and changed scope or risk.
4. Create or fork each ready child from its contract. Immediately record ID, route, ownership, and status. Isolate concurrent writers by worktree or branch.
5. Children may use routed subagents but may not create first-class tasks without explicit parent authority.
6. Wait through bounded snapshots. Children report `started`, `needs-attention`, and `completed`; the parent steers, resolves decisions, advances waves, and reports consolidated status.
7. Delegate integration and independent review as child tasks. Accept only aggregate evidence against the parent outcome.
8. Children return memory candidates; the parent alone invokes `$remember-the-work` Capture. Close or archive completed children when authorized.

Finish when every child is terminal, the ledger is current, integration and review are verified, and the parent reports outcome, evidence, residual risk, and next action.
