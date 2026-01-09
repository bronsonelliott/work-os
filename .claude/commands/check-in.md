---
description: Quick check-in workflow for capturing energy level, wins, friction, and priorities
---

Conduct a quick check-in interview and log it to `capture/check_in_log.md`.

## Interview Questions (ask one at a time)

1. **Energy level** (1-10): "What's your energy level right now, 1-10?"
2. **Wins**: "What wins are worth remembering from the past few days?"
3. **Friction**: "Any friction points or blockers?"
4. **What's Next**: "What's your priority for what's next?"
5. **Notes** (optional): "Anything else to note?"

## Format and Append Entry

Create this exact format and **append to the END** of `capture/check_in_log.md`:

```
## [YYYY-MM-DD]

**Energy:** [number with context if provided]

**Wins:**
[formatted response, preserve user's language]

**Friction:**
[formatted response, capture verbatim]

**What's Next:**
[formatted response]

**Notes:**
[only include if user provided notes, otherwise omit this section]
```

## Pattern Detection

After logging, check for:

**Low Energy Pattern**
- If energy < 4 AND there are 2+ low energy check-ins (<4) in past 30 days
- Alert: "This is your [X]rd low-energy check-in in the past month. Noticed pattern: burnout risk."

**Recurring Friction**
- If same friction mentioned in 3+ check-ins within 30 days
- Alert: "You've mentioned [friction theme] in 3 recent check-ins. This is a pattern worth addressing."

**Win Extraction**
- If wins were mentioned, ask: "Should I add any of these to your wins ledger?"
- If yes, use `/log-win` for each win

## Tone & Guidelines

- Quick and supportive, no judgment
- Preserve user's language and phrasing
- Don't over-format conversational answers
- Minimal answers are valid
- **CRITICAL**: Always append to END of file, never overwrite existing entries

Confirm completion: "Check-in logged. [mention any pattern if detected]"
