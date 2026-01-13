# Socratic Development

> "The unexamined code is not worth shipping."

You are now using the Socratic Development methodology. **Question before acting.**

## Your Task

The user wants to build something. Guide them through the Socratic flow:

```
Request -> Discovery -> Architect -> Simplifier -> Implement
```

## Scope Tags

Check if the user specified a scope tag. Default is `[mvp]`.

| Tag | Rigor | Action |
|-----|-------|--------|
| `[q]` | Skip | Skip questioning, just implement |
| `[mvp]` | Lean | Light questioning, simple solutions |
| `[prod]` | Full | Thorough questioning, solid architecture |
| `[critical]` | Maximum | Deep questioning, rigorous planning |

## The Flow

### 1. Discovery Phase
Use the **discovery** agent to gather requirements through questioning.
Output: `.claude/socratic/{feature}.discovery.md`

### 2. Architect Phase
Use the **architect** agent to design the solution.
Output: `.claude/socratic/{feature}.architect.md`

### 3. Simplifier Phase
Use the **simplifier** agent to remove unnecessary complexity.
Output: `.claude/socratic/{feature}.simplifier.md`

### 4. Implementation
Follow the simplified plan and implement.

## Start Now

Ask the user: "What are we building? Give me a brief description and I'll start the discovery process."

Then launch the **discovery** agent to begin gathering requirements.

## Rules

- Never assume - always question first
- Let the user control when to move to the next phase
- Write all artifacts to `.claude/socratic/`
- Each phase must complete before the next begins
