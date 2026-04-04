---
name: weekly-synthesis
description: Weekly review that synthesizes the past 7 days of conversations into an accumulation report. Tracks challenge/goal progress and updates the self-model.
allowed-tools: Read Write Glob Grep
---

# Weekly Synthesis

## Input
Read all of the following:
- All files in `logs/` from the past 7 days
- `me/goals.md`
- `me/challenges.md`
- `memory/long-term/self-model.md`
- `memory/long-term/patterns.md`
- Latest file in `memory/mid-term/`

## Processing Flow

1. **Extract themes** — identify emotions, topics, and frequent keywords from this week's logs
2. **Compare with last week** — what changed, continued, or emerged as new
3. **Challenge & Goal review** (see below)
4. **Generate report** — present "This Week's Accumulation Report"
5. **Propose self-model updates** — ask user for approval before writing

## Challenge & Goal Weekly Review

1. **Progress check:** For each active challenge/goal, extract related activity from this week's logs
2. **Status update proposals:** Propose status changes where progress occurred
3. **Neglect detection:** Highlight items not mentioned for 1+ weeks — ask whether to discuss next week
4. **New challenge extraction:** Propose challenge candidates from conversations not yet in `challenges.md`
5. **Close judgment:** Propose moving resolved challenges to "Resolved" section

## Output

### Report → `memory/mid-term/YYYY-WXX.md`

```markdown
## YYYY-WXX Accumulation Report

### Frequent Themes This Week
- ...

### Changes From Last Week
- ...

### Insights & Things Built Up This Week
- ...

### Challenge & Goal Progress
| Item | Last Week | This Week | Notes |
|------|-----------|-----------|-------|

### Alert: Items Not Discussed Recently
- ...

### Newly Emerging Challenge Candidates
- ...

### Self-model Update Proposals
- ...
```

### Updates (after user approval)
- `memory/long-term/self-model.md`
- `me/challenges.md`
- `me/goals.md`
- `memory/long-term/patterns.md` (if new patterns observed)
- `memory/long-term/growth-map.md` (append this week's growth)
