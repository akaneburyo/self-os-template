# self-os

> An experimental template by [@akaneburyo](https://github.com/akaneburyo) for building a personal coaching AI agent that records, reflects, and makes your growth visible.

This is a work-in-progress experiment. The idea is to use an AI agent as a dedicated coach and recorder — not to give answers, but to serve as **a mirror that makes accumulation visible**.

## What This Is

A repo-based system where:
- **You** define who you are (`me/`)
- **The agent** is configured to coach you through conversation (`agent/`)
- **Memory** accumulates over time through logs and weekly synthesis (`memory/`, `logs/`)

Conversations become assets. The more you use it, the more the agent understands your patterns, and the more your invisible effort becomes visible.

## Repo Structure

```
self-os/
├── CLAUDE.md                    # Agent persona & rules (Claude Code)
├── .claude/skills/              # Slash commands for Claude Code
│   ├── checkin/SKILL.md         # /checkin — daily check-in (~5 min)
│   ├── deep-session/SKILL.md   # /deep-session — ad-hoc deep dive
│   └── weekly-synthesis/SKILL.md # /weekly-synthesis — weekly review
│
├── me/                          # Who you are (primary source, written by you)
│   ├── profile.md               # Bio, values, personality
│   ├── career/                  # Career history (index + per-company details + resume)
│   ├── strengths.md             # Strengths & weaknesses
│   ├── goals.md                 # Goals with status tracking (dynamic)
│   └── challenges.md            # Current challenges with status (dynamic)
│
├── agent/
│   └── architecture.md          # Full design document
│
├── memory/                      # Agent memory (built up over time)
│   ├── long-term/               # Self-model, growth map, patterns
│   ├── mid-term/                # Weekly summaries
│   └── short-term/              # Temporary session storage
│
└── logs/                        # Conversation logs (YYYY/MM/YYYY-MM-DD.md)
```

## How It Works

1. **Check-in** — Short daily session to scan your energy, emotions, and focus
2. **Deep Session** — Ad-hoc conversation to dig into events, emotions, and patterns
3. **Weekly Synthesis** — Review the week's conversations, track challenge/goal progress, and update your self-model

See [agent/architecture.md](agent/architecture.md) for the full design.

## Getting Started

1. Fork or clone this repo
2. Fill in `me/` with your own information
3. Open the repo in Claude Code — it reads `CLAUDE.md` and skills automatically
4. Run `/checkin` for daily check-ins, `/deep-session` for deep dives, `/weekly-synthesis` for weekly reviews
5. Over time, your `memory/long-term/self-model.md` grows into a map of who you are

## Status

This is an early-stage experiment. Currently everything runs manually. Automation via GitHub Actions and a dedicated orchestrator are planned for future phases.
