# Thread Contracts

## Container decision

| Container | Use |
| --- | --- |
| Current task | One coherent outcome with coupled decisions or writes |
| Subagent | Bounded work that returns immediately to the current task |
| Child task | Durable, independently accepted work needing its own context, follow-up, approval, or worktree |

Prefer a new child task for clean independence; fork when accepted conversation context is load-bearing. Put concurrent code writers in separate worktrees and give each branch one owner.

## Child contract

```md
Task: <ID — outcome>
Parent / blockers:
Source of truth:
Skills:
Execution route:
Owns / must not touch:
Worktree / branch:
Done / evidence:
Return:
Child-task authority: none | explicitly bounded
```

## Parent ledger

```md
| ID | Thread | Outcome | Wave | Route | Owner | Status | Last report | Evidence |
```

Use `queued | running | needs-attention | integrating | verified | complete | failed | cancelled`.

## Required child reports

```md
Status: started | needs-attention | completed
Outcome / progress:
Changed surfaces:
Evidence:
Decisions or blocker:
Memory candidates:
Parent action:
```

Register `started` immediately after dispatch. Report `needs-attention` only for a parent decision, approval, route invalidation, or blocked dependency. A `completed` child must provide evidence and may not declare the parent outcome complete.
