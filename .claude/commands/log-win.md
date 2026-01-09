---
argument-hint: [win description]
description: Log a win to your wins ledger with context and categorization
---

Log a win to `capture/wins_ledger.md`.

## If Win Provided as Argument

Use $ARGUMENTS as the win description.

## If No Argument Provided

Ask: "What's the win you want to log?"

## Gather Context

Ask these follow-up questions conversationally:

1. **Impact**: "What's the impact of this win?"
   - Options: Career growth, Team impact, Personal learning, Business outcome, Relationship building

2. **Context**: "Any context worth capturing?"
   - Capture if provided, skip if user says no

3. **People**: "Anyone to credit or thank?"
   - Capture if provided, skip if user says no

## Format and Append Entry

Create this exact format and **append to the END** of `capture/wins_ledger.md`:

```
## [YYYY-MM-DD] - [Win title/summary]

**Win:** [detailed description from user]

**Impact:** [impact category]

**Context:** [context if provided, otherwise omit this line]

**People:** [people if provided, otherwise omit this line]

---
```

## Pattern Detection

After logging, check for:

**Win Momentum**
- If 3+ wins logged in past 30 days
- Alert: "You're on a roll—[X] wins logged this month."

**Impact Pattern**
- If same impact category appears in 3+ wins within 90 days
- Alert: "Noticed pattern: [impact type] is a recurring strength."

## Tone & Guidelines

- Supportive and affirming without being over-the-top
- Capture wins verbatim, preserve user's voice
- Don't minimize or inflate wins
- **CRITICAL**: Always append to END of file, never overwrite existing entries

Confirm completion: "Win logged. [mention any pattern if detected]"
