# Coaching Agent Design Document
_Created: 2026-04-04_

---

## 0. About This Document

This document defines the design of an AI Agent that coaches personal career, mental health, growth, and quality of life. It covers agent persona, skills, memory system, architecture, and repo structure.

Personal challenges and profile are managed under `me/`.

---

## 1. Design Philosophy

This agent functions not as "an answer provider" but as **"a mirror that makes accumulation visible."**

Conversations themselves become assets. As dialogue accumulates, the agent refines the user's self-model and articulates/structures "invisible growth."

### 3 Design Principles

1. **Visible Accumulation** — Make effort and growth visible over time through conversation logs and the memory system
2. **Designed for Continuity** — Build in rhythms and triggers so it's used daily
3. **Non-judgmental Relationship** — The agent neither criticizes nor praises; it asks questions so the user discovers on their own

---

## 2. Agent Persona Definition

### Role
Dedicated coach and recorder. Exists to help the user discover their own growth, changes, and patterns by asking questions, recording, and encouraging reflection.

### Core Personality
- Calm but does not tolerate vagueness
- Does not judge, compare, or rush
- Receives before answering
- Has consistent memory; can naturally ask "What's different from last week?"

### Coaching Style
- Socratic questioning ("What do you mean by that?" "Can you be more specific?")
- Helping name emotions ("Is that anxiety? Or frustration?")
- Pointing out patterns ("This topic has been coming up a lot recently")

### Prohibited Behaviors (Explicit in system prompt)
- Hollow affirmations like "You're doing great" or "It'll be fine"
- Rushing to conclusions
- Offering unsolicited solutions
- Starting from zero ignoring previous context

### System Prompt Skeleton

```
You are [username]'s dedicated coach and recorder.

## Your Role
- Ask questions to encourage self-reflection
- Record and summarize conversations, making accumulated growth visible
- Help the user notice their own patterns

## User Info
[Inject contents of me/profile.md here]

## Long-term Memory
[Inject contents of memory/long-term/self-model.md here]

## Recent Context
[Inject latest weekly summary from memory/mid-term/ here]

## Principles
- Do not judge, compare, or rush
- Always dig deeper into vague statements
- Don't hesitate to ask "What do you mean by that?"
- Receive emotions before trying to resolve them
- Never use hollow encouragement
```

---

## 3. Skills Design (3 Modes)

### 3-1. Check-in Skill

**Purpose:** Scan today's state in under 5 minutes. Build a habit of verbalizing emotions, energy, and concerns.

**Trigger:** Morning or evening (scheduled)

**Conversation Flow:**
1. "On a scale of 1-10, how's your energy today?"
2. "What's occupying your mind the most right now?"
3. "Do you want to talk about it today, or just log it?"

**Output:** Saved to session log (`logs/YYYY/MM/YYYY-MM-DD.md`).

**Prompt Skeleton:**
```
Mode: Check-in
Format: Ask one short question at a time. Never batch questions.
Limit: Complete within 5 exchanges.
On end: Summarize today's record and present it as "Today's Log".
```

---

### 3-2. Deep Session Skill

**Purpose:** Dig into events, emotions, and patterns together. Find the structure beneath surface-level concerns.

**Trigger:** When the user initiates a conversation (ad-hoc)

**Conversation Flow:**
1. Listen first (without interpreting)
2. "Can you tell me more about that?"
3. Name the emotion ("Is that anxiety? Or frustration?")
4. Pattern matching ("This has come up in a similar form before")
5. At session end, present "Today's Insight" in 1-2 sentences

**Prompt Skeleton:**
```
Mode: Deep Session
Format: One question at a time. Mirror the user's own words.
Prohibited: Offering solutions (unless the user asks)
On end: Present "Today's Insight" and propose additions to long-term memory.
```

---

### 3-3. Weekly Synthesis Skill

**Purpose:** Visualize "insights, changes, and accumulation" from the past 7 days. Directly addresses the "invisible effort" problem.

**Trigger:** Once a week (automated or user-initiated)

**Processing Flow:**
1. Load logs from the past 7 days
2. Extract emotions, themes, and frequent keywords
3. Compare with last week's summary (changes, continuations, new patterns)
4. Generate and present "This Week's Accumulation Report"
5. Propose updates to long-term memory (self-model.md)

**Output Format:**
```markdown
## This Week's Accumulation Report (W14)

### Frequent Themes This Week
- ...

### Changes From Last Week
- ...

### Insights & Things Built Up This Week
- ...

### Self-model Update Proposals
- ... (Approved items will be appended to self-model.md)
```

---

## 4. Memory System (3 Layers)

### 4-1. Short-term Memory (Within session)

- **Scope:** Retained only during the current session
- **Content:** Current conversation context, emotional flow, topics discussed
- **Update:** Summarized and written to mid-term memory at session end
- **Implementation:** Within the system prompt context window

### 4-2. Mid-term Memory (Weekly)

- **Scope:** Past 4-8 weeks
- **Content:** Weekly emotional trends, recurring themes, insights, changes
- **Update:** Auto-generated by Weekly Synthesis Skill
- **Implementation:** Managed as `memory/mid-term/YYYY-WXX.md` files
- **Format:**
  ```markdown
  ## YYYY-WXX Summary
  ### Emotional Trends
  ### Key Themes
  ### Insights
  ### Carryover to Next Week
  ```

### 4-3. Long-term Memory (Self-model)

- **Scope:** Indefinite (continuously updated)
- **Content:** Values, strengths, recurring patterns, growth timeline, core insights
- **Update:** Proposed by Weekly Synthesis Skill -> User approves -> Appended
- **Implementation:** `memory/long-term/self-model.md` (most important file)
- **Format:**
  ```markdown
  ## Self-model (Last updated: YYYY-MM-DD)

  ### Values
  ### Strengths (Emerged from conversations)
  ### Recurring Patterns (Positive)
  ### Recurring Patterns (Caution)
  ### Mental Triggers
  ### Growth Timeline
  ### Core Insights (Dated)
  ```

---

## 5. Overall Architecture

```
Trigger Layer
├── Morning/Evening (scheduled)
├── Ad-hoc (user-initiated)
└── Weekly (automated or manual)
        ↓
Agent Core
├── Persona (system prompt)
├── Orchestrator (mode selection, memory injection, synthesis)
│   ├── Inject me/ files
│   ├── Inject long-term/self-model.md
│   └── Inject mid-term/latest weekly summary
└── Skills (Check-in / Deep Session / Weekly Synthesis)
        ↕  fetch/save
Memory System
├── Short-term Memory (context window)
├── Mid-term Memory (memory/mid-term/*.md)
└── Long-term Memory (memory/long-term/self-model.md)
        ↓
Output
├── Conversation response
├── Session logs (logs/)
└── Growth report (weekly)
```

### Recommended Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| LLM | Claude API (Sonnet) | Long context, quality |
| Memory Storage | Markdown files (GitHub-managed) | Human-readable, git history becomes accumulation |
| Orchestration | Python scripts or Claude Code | Start simple |
| Scheduler | GitHub Actions | Free, declarative |
| Interface | Claude.ai (for now) -> Custom UI (future) | Get it running first |

---

## 6. GitHub Repo Structure

### Repo: `self-os`

```
self-os/
│
├── README.md                        # Purpose and usage of this repo
│
├── me/                              # Self-definition (primary source)
│   ├─�� profile.md                   # Bio, values, personality
│   ├── career/                      # Career info
│   │   ├── index.md                 # Summary, history, skills
│   │   ├── resume.md                # Achievement-based resume
│   │   └── {entry}.md               # Per-entry details (project, product, company, etc.)
│   ├── strengths.md                 # Strengths & weaknesses
│   ├── goals.md                     # Short/mid/long-term goals (dynamic)
│   └── challenges.md               # Current challenges (dynamic)
│
├── CLAUDE.md                        # Agent persona & rules (Claude Code)
│
├── .claude/skills/                  # Claude Code slash commands
│   ├── checkin/SKILL.md             # /checkin — daily check-in
│   ├── deep-session/SKILL.md       # /deep-session — ad-hoc deep dive
│   └── weekly-synthesis/SKILL.md   # /weekly-synthesis — weekly review
│
├── agent/                           # Design reference
│   └── architecture.md              # This document (design)
��
├── memory/                          # Memory system data
│   ├── long-term/
│   │   ├── self-model.md            # Self-model (most important file)
│   ���   ├── growth-map.md            # Growth timeline
│   │   └── patterns.md              # Recurring patterns
│   ├── mid-term/
│   │   └── 2026-W14.md              # Weekly summary
│   └── short-term/                  # Temporary session log storage
│
├── logs/                            # Conversation logs
│   └── 2026/
│       └── 04/
│           └── 2026-04-04.md
│
└── .github/
    └── workflows/
        └── weekly-synthesis.yml     # Weekly synthesis automation (future)
```

### Why separate me/ and agent config

`me/` is primary information you write directly. `CLAUDE.md` and `.claude/skills/` define how the agent reads and behaves based on it. Mixing these makes authorship ambiguous and breaks update/management workflows.

---

## 7. Implementation Roadmap

### Phase 1 — Manual operation (~2 weeks)
- [ ] Create `self-os` repo
- [ ] Fill `me/` folder by hand (profile, career, goals)
- [ ] Create `agent/persona.md` based on this document
- [ ] Create 3 files under `agent/skills/`
- [ ] Try manual check-in using Persona prompt on Claude.ai
- [ ] Create initial version of `memory/long-term/self-model.md`

### Phase 2 — Connect memory (~1 month)
- [ ] Build habit of saving session logs to `logs/`
- [ ] Run weekly synthesis manually, update `mid-term/`
- [ ] Weekly update of `self-model.md` (approval flow)
- [ ] Inject mid-term memory into system prompt, verify conversation continuity

### Phase 3 — Automation (~3 months)
- [ ] Implement Orchestrator with Python / Claude Code
- [ ] Automate weekly synthesis via GitHub Actions
- [ ] Implement check-in scheduler
- [ ] Visualize "growth map" (timeline graph of growth-map.md)

---

## 8. Definition of Success

The state where this agent is working:

> **In 3 months, when you open `memory/long-term/self-model.md`, you feel "I've built up this much over the past 3 months"**

The starting problem — "invisible effort" — is resolved through the mechanisms of recording, memory, and reflection.

---

_This document is stored as `self-os/agent/architecture.md`._
