# Founder Mode Development Workflow

## Golden Rule

**NEVER WRITE CODE IMMEDIATELY.**

When a user requests a feature, bug fix, refactor, or any code change - stop. Do not write a single line of production code until you have a plan rated 9+ by the judge.

## The Planning Loop

### Step 1: Receive Request
When the user asks for any code change, acknowledge the request but do NOT start coding.

### Step 2: Solution Architect Plans
Use the `solution-architect` agent to create a detailed plan:
- Analyze the problem and requirements
- Research existing patterns in the codebase
- Design the solution with trade-offs considered
- Document everything in a `.md` file (e.g., `feature-name-plan.md`)

### Step 3: Solution Architect Judge Rates
Use the `solution-architect-judge` agent to evaluate the plan:
- Scores across 6 dimensions (Completeness, Feasibility, Scalability, Maintainability, Security, Clarity)
- Overall score from 0-10
- Creates a `.judge.md` assessment file

### Step 4: Check Score
- **Score < 9**: Return to Step 2. The architect must revise the plan based on judge feedback.
- **Score 9+**: Proceed to implementation.

```
         ┌──────────────┐
         │   Request    │
         └──────┬───────┘
                │
                ▼
         ┌──────────────┐
    ┌───▶│  Architect   │
    │    │   Plans      │
    │    └──────┬───────┘
    │           │
    │           ▼
    │    ┌──────────────┐
    │    │    Judge     │
    │    │    Rates     │
    │    └──────┬───────┘
    │           │
    │     ┌─────┴─────┐
    │     │  Score?   │
    │     └─────┬─────┘
    │      <9   │   9+
    │    ┌──────┘    │
    │    │           │
    └────┘           ▼
              ┌──────────────┐
              │  Implement   │
              │    Code      │
              └──────────────┘
```

## Implementation Phase

Only after achieving a 9+ rating:

1. Read the approved plan `.md` file
2. Follow the plan step-by-step
3. Implement code changes as specified
4. Do not deviate from the plan without re-planning

## Agents

| Agent | Purpose | Output |
|-------|---------|--------|
| `solution-architect` | Creates detailed implementation plans | `*-plan.md` files |
| `solution-architect-judge` | Evaluates and scores plans | `*.judge.md` files |

## Why This Workflow?

- Forces thorough thinking before coding
- Catches architectural issues early
- Creates documentation as a byproduct
- Reduces wasted effort from poor planning
- Ensures quality through iteration
