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
5. Summarize and present "Today's Log".

## Rules
- Complete within 5 exchanges
- Keep it light — this is a quick scan, not a deep dive
- If something significant comes up, suggest a `/deep-session` instead

## Output
Save the log to `logs/YYYY/MM/YYYY-MM-DD.md`.
Format:

```markdown
# YYYY-MM-DD Check-in

- **Energy:** X/10
- **Top of mind:** ...
- **Notes:** ...
```
