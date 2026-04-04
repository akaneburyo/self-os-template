---
name: checkin
description: Daily check-in to scan energy, emotions, and focus in under 5 minutes. Use when starting or ending the day.
allowed-tools: Read Write Glob
argument-hint: "[morning|evening]"
---

# Check-in Session

Read the following files before starting:
- `me/goals.md`
- `me/challenges.md`
- `memory/long-term/self-model.md`
- Latest file in `memory/mid-term/`

## Flow

Ask one question at a time. Never batch questions.

1. "On a scale of 1-10, how's your energy today?"
2. "What's occupying your mind the most right now?"
3. "Do you want to talk about it today, or just log it?"
4. If the user wants to talk, ask 1-2 follow-up questions max.
5. **Values check** (1 question): "Does what you're focusing on today feel connected to what actually matters to you?"
6. Summarize and present "Today's Log".

## Rules
- Complete within 5-6 exchanges
- Keep it light — this is a quick scan, not a deep dive
- If something significant comes up, suggest a `/deep-session` instead

## ACT Lens (Silent Analysis)

While listening, silently observe for the following. Do NOT label or confront directly during check-in — just note in the log.

**Cognitive Fusion markers** (thoughts treated as facts):
- "I am..." statements (identity fusion: "I'm the kind of person who...")
- "I can't..." (ability fusion)
- "I must / should / have to..." (rule fusion)
- "I'll always / never..." (permanence fusion)

**Experiential Avoidance markers** (moving away from difficult experience):
- "It's fine" / "not a big deal" when energy is low
- Deflecting to tasks/plans instead of naming feelings
- Over-explaining or intellectualizing instead of feeling

**Values-Action Gap markers**:
- What they're focused on vs. what they said matters to them (cross-reference `me/goals.md` and `self-model.md` Values)
- "I should be doing X" language without intrinsic motivation behind it

**Cognitive distortions** (flag if clearly present):
- All-or-nothing ("either I do it perfectly or it's pointless")
- Catastrophizing ("this will ruin everything")
- Should statements ("I should already be...")
- Emotional reasoning ("I feel like a failure, so I must be one")

## Output

Save the log to `logs/YYYY/MM/YYYY-MM-DD.md`.

```markdown
# YYYY-MM-DD Check-in

- **Energy:** X/10
- **Top of mind:** ...
- **Values alignment:** (aligned / drifted / unclear)
- **Notes:** ...

## ACT Observation
- **Detected patterns:** (fusion / avoidance / values-gap / none)
- **Flags:** (specific language or themes to watch — leave blank if none)
```
