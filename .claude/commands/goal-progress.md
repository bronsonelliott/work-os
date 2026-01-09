---
description: Check progress against annual and quarterly goals based on work logs
argument-hint: (no arguments - automated analysis)
---

# Goal Progress Check

A quick 5-minute automated check of your progress against stated annual and quarterly goals.

## Usage

- `/goal-progress` - Run full goal progress analysis

## What This Does

Claude automatically reads:
1. `goals/annual_goals_FY26.md` - Your declared goals for the year
2. `goals/quarterly_focus.md` - Your current quarter focus
3. `capture/work_log.md` - Your actual work (YTD or recent months)
4. `capture/wins_ledger.md` - Your logged wins

Then assesses progress on each goal:
- **On track** - Work clearly advancing this goal
- **Behind** - Little/no evidence of progress
- **Ahead** - More progress than expected
- **Unclear** - Can't tell from available data

## Output

Claude generates:

```markdown
# Goal Progress Check - [Date]

## Annual Goals (FY26)

### Goal 1: [Goal Title]
**Status:** [On Track / Behind / Ahead / Unclear]

**Evidence:**
- [Work from logs that advances this goal]
- [Wins that relate to this goal]

**Assessment:** [Is this where you expected to be at this point in the year?]

---

### Goal 2: [Goal Title]
**Status:** [On Track / Behind / Ahead / Unclear]

**Evidence:**
- [Work from logs]

**Assessment:** [Commentary]

---

## Quarterly Focus (Q[X])

**Your Stated Focus:** [from quarterly_focus.md]

**Progress on Focus:**
[Evidence from work_log showing progress on quarterly priorities]

**Assessment:** [On track / needs adjustment]

---

## Summary

**Goals on track:** X / Y
**Goals behind:** A / Y
**Goals ahead:** B / Y

**Recommendation:** [Accelerate / Adjust expectations / Refocus]
```

## Three Recommendations

Based on the analysis, Claude offers one of three paths:

### 1. **Accelerate** (Goals behind but achievable)
- Which goals need more attention
- What to stop/reduce to create space
- Specific actions to catch up

**When:** You're behind but have time to catch up with focus.

### 2. **Adjust Expectations** (Goals unrealistic given reality)
- Which goals to scale back
- Which goals to defer
- How to reset expectations

**When:** Original goals were too ambitious or circumstances changed.

### 3. **Refocus** (Priorities have shifted)
- Which goals no longer matter
- Which new priorities have emerged
- Whether to update `goals/annual_goals_FY26.md`

**When:** Your actual work shows different priorities than stated goals.

## When to Use This

- **Mid-quarter check-in** - Quick pulse on progress
- **End of quarter** - Before quarterly reflection
- **Before manager 1:1s** - Know your goal status
- **Mid-year review prep** - Assess H1 progress
- **When you feel behind** - Understand if it's real or just feeling

## Smart Analysis

Claude intelligently:
- Accounts for time of year (don't expect 100% progress in Q1)
- Connects work to goals even if you didn't explicitly link them
- Flags shadow goals getting more attention than declared goals
- Notes if quarterly focus conflicts with annual goals
- Identifies if wins align with goals

## If Data is Missing

- **No annual goals:** "You don't have annual goals set. Want to run /goal-setting first?"
- **No work logs:** "Your work_log.md is empty. Can't assess progress without work data. Want to run /monthly-log?"
- **Stale work logs:** "Your most recent work log is from [date]. Progress check will be based on old data."

## Critical Rules

- **NEVER make up progress** - Only assess based on actual logged work
- Be honest about "Behind" status - it's data, not judgment
- If a goal has zero evidence in logs, mark as "Unclear" not "Behind"
- Account for time of year in assessment (Q1 vs Q4)
- Save analysis to `analysis/goal_progress_[date].md` for tracking over time
- Always offer one of the three recommendations

## After Analysis

Claude asks:

1. **If goals are on track:** "Want to see what's working? I can highlight your success patterns."

2. **If goals are behind:** "Want help creating an acceleration plan? Or should we adjust expectations?"

3. **If goals are unclear:** "I can't see evidence of progress on these goals. Want to refocus, or just haven't logged relevant work yet?"

## Tone

- Honest but supportive
- "Behind" is information, not failure
- Celebrate "on track" and "ahead" progress
- Assume good reasons if goals shifted
- Make adjusting expectations feel as valid as accelerating
