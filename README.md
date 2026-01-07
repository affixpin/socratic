# Founder Mode

A Claude Code configuration framework for solo founders to run an AI-powered startup team.

## The Vision

Replace your startup team with a team of specialized AI subagents. As a founder, you become the manager of AI agents instead of human employees.

```
                    ┌─────────────┐
                    │   FOUNDER   │
                    │  (You)      │
                    └──────┬──────┘
                           │ manages
           ┌───────────────┼───────────────┐
           │               │               │
           ▼               ▼               ▼
    ┌─────────────┐ ┌─────────────┐ ┌─────────────┐
    │  Architect  │ │  Frontend   │ │  Marketing  │
    │    Team     │ │    Team     │ │    Team     │
    └─────────────┘ └─────────────┘ └─────────────┘
           │               │               │
    ┌──────┴──────┐ ┌──────┴──────┐ ┌──────┴──────┐
    │   Agent  ◄──►  Judge   │ │   Agent  ◄──►  Judge   │ │   Agent  ◄──►  Judge   │
    └─────────────┘ └─────────────┘ └─────────────┘
```

## Core Concept: Agent-Judge Pairs

Every subagent comes in a pair:

| Role | Agent | Judge |
|------|-------|-------|
| **Purpose** | Does the work | Reviews the work |
| **Output** | Creates artifacts | Rates & critiques |
| **Mindset** | Creative, productive | Critical, quality-focused |

The pair creates a feedback loop:

```
Agent creates → Judge rates → Score < 9? → Agent revises → Judge rates → ...
                                   ↓
                              Score 9+? → Done, approved
```

## Why Pairs?

A single agent has no quality control. It will:
- Miss edge cases
- Make assumptions
- Produce inconsistent quality

The judge forces iteration until quality standards are met. This mimics how real teams work: developers have code reviewers, writers have editors, designers have critics.

## Current Agents

### Solution Architecture Team
- `solution-architect` - Plans features, designs systems, documents approaches
- `solution-architect-judge` - Evaluates plans on 6 dimensions, scores 0-10

## Roadmap: Future Teams

Build out agent pairs for each startup function:

| Team | Agent | Judge | Status |
|------|-------|-------|--------|
| Architecture | `solution-architect` | `solution-architect-judge` | Done |
| Frontend | `frontend-dev` | `frontend-reviewer` | Planned |
| Backend | `backend-dev` | `backend-reviewer` | Planned |
| Testing | `qa-engineer` | `qa-lead` | Planned |
| DevOps | `devops-engineer` | `devops-reviewer` | Planned |
| Copywriting | `copywriter` | `editor` | Planned |
| Marketing | `marketer` | `marketing-strategist` | Planned |
| Product | `product-manager` | `product-lead` | Planned |

## Setup

1. Clone this repo
2. Symlink to your home directory:
   ```bash
   ln -s /path/to/founder-mode/.claude ~/.claude
   ```
3. All Claude Code sessions now use this config globally

## Directory Structure

```
.claude/
├── CLAUDE.md              # Global instructions (the workflow)
├── settings.json          # Permissions & settings
├── agents/                # Subagent definitions
│   ├── solution-architect.md
│   └── solution-architect-judge.md
└── .gitignore
```

## Working Files

Agents output plans to `.claude/founder-mode-plans/` in each project:

```
your-project/
└── .claude/
    └── founder-mode-plans/
        ├── auth-feature-plan.md
        └── auth-feature-plan.judge.md
```

These are **temporary working files**—gitignored by default. Add this to your project's `.gitignore`:

```
.claude/founder-mode-plans/
```

## The Founder's Job

You don't write code. You don't design systems. You:

1. **Define goals** - What needs to be built?
2. **Delegate to agents** - "Use solution-architect to plan this feature"
3. **Review approved work** - Only look at 9+ rated outputs
4. **Make decisions** - Choose between options agents present
5. **Manage priorities** - Direct which agent works on what

## Philosophy

> "The best founders don't do the work. They build systems that do the work."

This config turns Claude into that system. Each agent pair is a self-improving unit that iterates until quality is achieved. Your job is orchestration, not execution.

## Contributing

Add new agent pairs by creating two files in `.claude/agents/`:
- `{role}.md` - The doer
- `{role}-judge.md` - The reviewer

Follow the existing patterns. Every agent needs its judge.

## License

MIT
