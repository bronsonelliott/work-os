---
description: Log important decisions with tradeoff analysis and constraint checking
argument-hint: "[decision description]" or empty for interactive mode
---

# Log Decision

Quick 2-3 minute workflow to capture decisions you're making, the tradeoffs involved, and whether they align with your stated constraints.

## Usage

- `/log-decision "Declined to lead the platform migration project"` - Quick mode with decision text
- `/log-decision` - Interactive mode, Claude asks questions

## What This Does

Captures decisions in a structured format:
- What you decided (the actual choice made)
- Why you decided this (reasoning and context)
- What tradeoff you accepted (what you're giving up)
- Any regrets or concerns (honest reflection)

After logging, Claude:
- Checks the decision against your `foundation/values_and_constraints.md`
- Flags if the decision violates stated constraints
- Saves to `capture/decision_log.md` with date header
- Tracks decision patterns over time

## Interview Flow

Claude asks:

1. **What did you decide?** (The actual choice: yes/no, A vs B, stop/start/continue)
2. **Why did you decide this?** (Your reasoning, what influenced it)
3. **What tradeoff are you accepting?** (What you're giving up by choosing this)
4. **Any regrets or concerns?** (Honest gut check - is this sitting right with you?)

You can be conversational. Claude captures it verbatim.

## Constraint Checking

After you answer, Claude:
1. Reads your `foundation/values_and_constraints.md`
2. Checks if this decision violates any stated constraints
3. If violation detected, Claude flags it: "This seems to conflict with your constraint: [constraint]. Is this a conscious exception or should we revisit?"
4. You decide whether to proceed, revise, or update constraints

## Output Format

Entries are appended to `capture/decision_log.md`:

```markdown
## [Date] - [Decision Title]

**Decision:** [what you decided]

**Reasoning:** [why]

**Tradeoff:** [what you're giving up]

**Regrets/Concerns:** [honest reflection]

**Constraint Check:** [clean / flagged: violated constraint X]
```

## Why This Matters

Tracking decisions helps you:
- See patterns in what you say yes/no to
- Understand if you're honoring your stated constraints
- Build evidence for career direction shifts
- Reflect on tradeoffs you're consistently making

## Critical Rules

- **NEVER overwrite existing decision_log.md** - Always append
- Capture decision reasoning verbatim - no editorializing
- ALWAYS run constraint check before saving
- Flag constraint violations clearly but non-judgmentally
- If decision_log.md doesn't exist, create it with proper header
- Keep it quick - this should be 2-3 minutes max

## Tone

- Non-judgmental about decisions
- Supportive when flagging constraint violations
- Treat regrets and concerns as valuable data, not weakness
- Make constraint checking feel helpful, not like policing
