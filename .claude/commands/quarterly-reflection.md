---
description: End-of-quarter reflection interview to reset thinking and set next quarter focus
argument-hint: "[quarter]" (e.g., "Q2" or empty for auto-detect)
---

# Quarterly Reflection

A 15-20 minute end-of-quarter interview that helps you reset your thinking, identify patterns, and set focus for the next quarter.

## Usage

- `/quarterly-reflection` - Auto-detects current quarter, reflects on it
- `/quarterly-reflection "Q2"` - Reflect on specific quarter

## What This Does

Conducts a structured interview about the quarter that just ended:
- What actually moved this quarter
- What mattered most (vs what you thought would matter)
- Where you over/under-rotated
- Surprises (positive and negative)
- Energy patterns
- Stakeholder relationships
- What needs to change next quarter

After the interview, Claude:
- Updates `goals/quarterly_focus.md` with next quarter's focus
- Updates `synthesis/pattern_recognition.md` with quarterly patterns
- Updates `capture/energy_log.md` with energy insights
- Shows you the outputs for review

## Interview Flow

Claude asks these 10 questions:

1. **What actually moved this quarter?** (Projects, initiatives, outcomes)
2. **What mattered most?** (What had real impact, what was just noise)
3. **Where did you over-rotate?** (What got too much time/energy relative to value)
4. **Where did you under-rotate?** (What deserved more attention but didn't get it)
5. **What surprised you positively?** (Unexpected wins, breakthroughs, good outcomes)
6. **What surprised you negatively?** (Unexpected challenges, failures, disappointments)
7. **How was your energy this quarter?** (High/low points, what drained vs energized you)
8. **Which stakeholder relationships mattered most?** (Who influenced outcomes, who you need to invest in)
9. **What needs to change next quarter?** (Stop, start, continue)
10. **What's your one focus for next quarter?** (If you could only move one thing, what is it?)

You can answer conversationally. Claude synthesizes into the outputs.

## What Gets Updated

### 1. `goals/quarterly_focus.md` (Next Quarter Section)
```markdown
## Q[X] FY26 Focus

**Primary Focus:** [your one focus answer]

**Key Initiatives:**
- [synthesized from "what needs to change"]

**Stop Doing:**
- [from over-rotation answers]

**Energy Management:**
- [from energy patterns]

**Stakeholder Investments:**
- [from stakeholder answers]
```

### 2. `synthesis/pattern_recognition.md`
Adds quarterly patterns:
- Over/under-rotation patterns
- Energy patterns
- Surprise patterns
- Stakeholder patterns

### 3. `capture/energy_log.md`
Logs quarterly energy data for trend analysis

## When to Use This

- **End of each quarter** (Dec, Mar, Jun, Sep)
- When you feel "off" mid-quarter and need to reset
- Before quarterly planning with your manager
- When preparing for performance reviews

## Critical Rules

- **NEVER overwrite existing sections** in quarterly_focus.md - append new quarter section
- Create synthesis/pattern_recognition.md if it doesn't exist
- Create capture/energy_log.md if it doesn't exist
- Auto-detect current quarter from system date if not provided
- Show all outputs before saving - user may want to edit
- If user hasn't done monthly logs this quarter, warn: "Your work_log.md is sparse. Your reflection might be harder without recent logs."

## After Reflection

Claude offers:
1. "Want to see drift analysis now?" (compare this quarter's work vs stated intent)
2. "Want to run /monthly-log for this month?" (if not done yet)
3. "Here's what I'm updating. Review before I save?"

## Tone

- Reflective and curious, not judgmental
- Celebrate what worked, learn from what didn't
- Acknowledge over/under-rotations without guilt
- Treat energy data as valuable signal
- Make next quarter feel like a fresh start
