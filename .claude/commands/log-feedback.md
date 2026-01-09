---
argument-hint: [feedback description]
description: Log feedback to your feedback ledger with source and pattern tracking
---

Log feedback to `capture/feedback_ledger.md`.

## If Feedback Provided as Argument

Use $ARGUMENTS as the feedback description.

## If No Argument Provided

Ask: "What's the feedback you want to log?"

## Gather Context

Ask these follow-up questions conversationally:

1. **Source**: "Who gave you this feedback?"
   - Capture name/role if provided, or "Self-reflection" if user generated

2. **Context**: "What's the context around this feedback?"
   - Capture if provided, skip if user says no

3. **Action**: "Any immediate actions you're considering?"
   - Capture if provided, skip if user says no

## Format and Append Entry

Create this exact format and **append to the END** of `capture/feedback_ledger.md`:

```
## [YYYY-MM-DD] - [Feedback summary]

**Feedback:** [exact feedback as shared, preserve user's language]

**Source:** [who provided it]

**Context:** [context if provided, otherwise omit this line]

**Action:** [actions if provided, otherwise omit this line]

**Status:** Active

---
```

## Pattern Detection

After logging, check for:

**Recurring Theme**
- If similar feedback theme appears in 2+ entries within 90 days
- Alert: "You've received similar feedback about [theme] [X] times in the past 90 days. This is a pattern worth addressing."

**Self-Reflection Pattern**
- If 3+ "Self-reflection" feedback entries in past 30 days
- Alert: "You've been actively self-reflecting—[X] feedback entries this month."

**Actionable Feedback**
- If feedback has action items, ask: "Want to add this to your quarterly focus or goals?"

## Tone & Guidelines

- Non-judgmental and supportive
- Capture feedback verbatim without editorializing
- Don't minimize or inflate feedback
- Treat self-reflection same as external feedback
- **CRITICAL**: Always append to END of file, never overwrite existing entries

Confirm completion: "Feedback logged. [mention any pattern if detected]"
