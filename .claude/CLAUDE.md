# Founder Mode Development Workflow

## Scope Tags

Users control the rigor level with scope tags. **Default is `[mvp]` when no tag is specified.**

| Tag | Name | Planning | Threshold | Use When |
|-----|------|----------|-----------|----------|
| `[q]` | Quick | Skip entirely | - | Typos, one-liners, obvious fixes |
| `[mvp]` | MVP | Lean planning | 8+ | Most features, default behavior |
| `[prod]` | Production | Full rigor | 9+ | Core systems, complex refactors |
| `[critical]` | Critical | Max scrutiny | 9.5+ | Security, payments, data integrity |

**Examples:**
- `[q] fix the typo in header` → Just fix it, no planning
- `add dark mode` → MVP (default), lean plan, 8+ to pass
- `[prod] refactor auth system` → Full planning loop, 9+ required
- `[critical] implement payment processing` → Maximum rigor, 9.5+ required

## The Planning Loop

```
         ┌──────────────┐
         │   Request    │
         └──────┬───────┘
                │
          ┌─────┴─────┐
          │  Scope?   │
          └─────┬─────┘
           [q]  │  [mvp]/[prod]/[critical]
          ┌─────┘     │
          │           ▼
          │    ┌──────────────┐
          │    │  Architect   │◀──┐
          │    │   Plans      │   │
          │    └──────┬───────┘   │
          │           │           │
          │           ▼           │
          │    ┌──────────────┐   │
          │    │    Judge     │   │
          │    │    Rates     │   │
          │    └──────┬───────┘   │
          │           │           │
          │     ┌─────┴─────┐     │
          │     │ Threshold?│     │
          │     └─────┬─────┘     │
          │      fail │  pass     │
          │           └──────┐    │
          │           │      │    │
          │           └──────┘    │
          │                  │
          └────────┬─────────┘
                   ▼
            ┌──────────────┐
            │  Implement   │
            │    Code      │
            └──────────────┘
```

### For `[q]` (Quick) Requests
Skip planning entirely. Just implement the change directly.

### For `[mvp]`, `[prod]`, `[critical]` Requests

**Step 1:** Identify scope (default: `[mvp]`)

**Step 2:** Solution Architect creates plan calibrated to scope

**Step 3:** Solution Architect Judge evaluates with scope-appropriate criteria

**Step 4:** Check against threshold:
- `[mvp]`: 8+ passes
- `[prod]`: 9+ passes
- `[critical]`: 9.5+ passes

**Step 5:** If below threshold, architect revises. If passes, implement.

## Implementation Phase

After passing the threshold:

1. Read the approved plan `.md` file
2. Follow the plan step-by-step
3. Implement code changes as specified
4. Do not deviate from the plan without re-planning

## Agents

| Agent | Purpose | Output |
|-------|---------|--------|
| `solution-architect` | Creates detailed implementation plans | `*-plan.md` files |
| `solution-architect-judge` | Evaluates and scores plans | `*.judge.md` files |

## File Storage

All agent-generated plans go to: `.claude/founder-mode-plans/`

```
project/
└── .claude/
    └── founder-mode-plans/
        ├── feature-name-plan.md
        └── feature-name-plan.judge.md
```

These files are **temporary working documents**—gitignored, not committed. Once implementation is complete, they can be deleted.

## Why This Workflow?

- Forces thorough thinking before coding
- Catches architectural issues early
- Creates documentation as a byproduct
- Reduces wasted effort from poor planning
- Ensures quality through iteration
