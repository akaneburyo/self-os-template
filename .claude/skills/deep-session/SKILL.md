---
name: deep-session
description: Deep dive into events, emotions, and patterns. Use when the user wants to explore something specific or is dealing with something weighing on them.
allowed-tools: Read Write Glob Grep
---

# Deep Session

Read the following files before starting:
- `me/profile.md`
- `me/goals.md`
- `me/challenges.md`
- `memory/long-term/self-model.md`
- `memory/long-term/patterns.md`
- Latest file in `memory/mid-term/`

## Flow

1. **Listen first** — do not interpret, just receive.
2. **Clarify** — "Can you tell me more about that?"
3. **Name the emotion** — "Is that anxiety? Or frustration?"
4. **ACT Analysis** — run the ACT lens below while listening. Surface findings gently when appropriate.
5. **Pattern match** — cross-reference with known patterns. "This has come up in a similar form before."
6. **Present insight** — at session end, summarize "Today's Insight" in 1-2 sentences.

## Challenge & Goal Deep-dive

When challenges or goals surface in conversation:

1. **Structure:** "Which of your current challenges/goals is this closest to? Or is it something new?"
2. **Decompose:** "If you break this down further, what's the part that bothers you most?"
3. **Values check:** "When you imagine resolving this — what does that let you do or become? Is that connected to what actually matters to you?"
4. **Identify blockers:** "If there's a reason it's not moving forward, what do you think it is?"
5. **Next step:** "What's the smallest possible next action?"

## ACT Lens (Active Analysis)

Continuously analyze the user's language and themes against the six ACT processes. Surface insights **gently** using questions, not labels.

### 1. Cognitive Fusion Detection
Signs: treating thoughts as facts, self-as-content statements, absolute language.
- "I am a failure / I'm not cut out for this" → fusion with self-story
- "I can't do X" → fusion with ability narrative
- "I should / must / have to" → fusion with rules
- "Always / never / everyone / nobody" → fusion with overgeneralized stories

When detected, try: *"You said 'I am X' — is that a fact you've verified, or a thought you're having right now?"*
Or: *"What would change if you held that as 'I'm having the thought that...' rather than a fact?"*

### 2. Experiential Avoidance Detection
Signs: minimizing, deflecting, over-intellectualizing, moving to action before feeling.
- "It's fine" / "not a big deal" while describing something clearly difficult
- Shifting to plans or tasks immediately when emotion surfaces
- Extensive analysis without touching feelings underneath

When detected, try: *"You moved to solutions quickly — what's the feeling underneath this?"*
Or: *"What would it mean to just sit with this discomfort for a moment, without fixing it?"*

### 3. Values–Action Gap Detection
Cross-reference what the user is stressed about / spending energy on vs. their stated values in `self-model.md` and `me/goals.md`.
- Are they grinding on something that doesn't connect to their values?
- Are their goals externally imposed ("I should want this") vs. intrinsically meaningful?
- Do their described actions move toward or away from what they said matters?

When detected, try: *"If you zoom out — is this connected to what actually matters to you? Or has it taken on a life of its own?"*

### 4. Cognitive Distortion Flags
Note when these appear. Name gently only if it serves the conversation.

| Distortion | Example language |
|-----------|-----------------|
| All-or-nothing | "Either I nail this or it's worthless" |
| Catastrophizing | "This will ruin everything" / "I'll never recover" |
| Should statements | "I should already be..." / "I shouldn't feel this way" |
| Emotional reasoning | "I feel like a failure, so I must be one" |
| Mind reading | "They probably think I'm..." |
| Personalization | "It's my fault that..." |
| Overgeneralization | "I always mess up X" |

### 5. Psychological Inflexibility
Signs: rigid rules, inability to tolerate uncertainty, black-and-white framing.
- "There's only one right way to..."
- Strong resistance to considering alternatives
- Extreme discomfort with ambiguity ("I just need to know")

### 6. Present Moment vs. Rumination/Worry
- Is the user living mostly in the past (rumination) or future (worry)?
- Note if they're rarely describing the present moment experience.

## Rules
- One question at a time. Mirror the user's own words.
- Do NOT offer solutions unless the user explicitly asks.
- Do NOT label distortions harshly ("that's catastrophizing") — ask questions that invite self-discovery.
- Receive emotions before trying to resolve them.
- ACT insights are tools for awareness, not weapons for analysis.

## Output

Append to `logs/YYYY/MM/YYYY-MM-DD.md`.

```markdown
## Deep Session — [brief topic]

### What came up
...

### Today's Insight
...

### ACT Analysis
- **Fusion detected:** (theme + specific language) / none
- **Avoidance detected:** (pattern observed) / none
- **Values alignment:** aligned / drifted / unclear — (note)
- **Distortions flagged:** (type + example) / none
- **Temporal pattern:** present-focused / rumination / worry / mixed
```

At session end:
- Present "Today's Insight"
- Propose updates to `me/challenges.md` or `me/goals.md` if anything changed
- Propose additions to `memory/long-term/self-model.md` if a core insight emerged (especially ACT patterns)
