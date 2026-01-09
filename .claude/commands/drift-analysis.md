---
description: Compare stated career intent vs actual work to identify drift and misalignment
argument-hint: (no arguments - automated analysis)
---

# Drift Analysis

A 10-minute automated analysis that compares your **stated intent** (what you say matters) vs **actual work** (what you're actually doing) to surface misalignment.

## Usage

- `/drift-analysis` - Run full drift analysis

## What This Does

Claude automatically reads:
1. `foundation/career_intent_FY26.md` - Your stated career direction
2. `foundation/values_and_constraints.md` - Your stated constraints
3. `goals/annual_goals_FY26.md` - Your declared goals and shadow goals
4. `capture/work_log.md` - Your actual work (last 3 months)
5. `capture/decision_log.md` - Your actual decisions

Then compares them across three dimensions:

### 1. **Intent vs Reality Drift**
- What you say you want your career to be about
- vs what you're actually spending time on
- **Example:** You say you want to "build strategic skills" but 80% of work log is tactical execution

### 2. **Constraint Violations**
- What you said you won't do (your constraints)
- vs what you're actually doing (from decision_log and work_log)
- **Example:** You have a constraint "no after-hours work" but work_log shows consistent evening work

### 3. **Goal Allocation Drift**
- Your declared goals vs shadow goals (and % allocation you set)
- vs actual time/energy allocation (from work_log)
- **Example:** You allocated 60% to declared goals, 40% to shadow goals, but work shows 30/70 split

## Output

Claude generates a drift analysis showing:

```markdown
# Drift Analysis - [Date]

## Intent vs Reality

**Your Stated Intent:**
[from career_intent_FY26.md]

**Your Actual Work (Last 3 Months):**
[synthesized from work_log.md]

**Drift Detected:**
- [specific gap 1]
- [specific gap 2]

**Drift Severity:** [Low / Medium / High]

---

## Constraint Violations

**Your Stated Constraints:**
[from values_and_constraints.md]

**Constraint Check:**
- ✓ [constraint being honored]
- ⚠️ [constraint being violated - evidence from logs]

---

## Goal Allocation Drift

**Your Declared Allocation:**
- Declared goals: X%
- Shadow goals: Y%

**Actual Allocation (Last 3 Months):**
- Declared goals: A%
- Shadow goals: B%

**Drift:** [X-A percentage points]

---

## What This Means

[Claude's synthesis: Is this drift concerning? Is it temporary? Is it a signal?]

---

## Three Options

1. **Update your intent** - Your actual work reflects what truly matters now. Update foundation docs to match reality.

2. **Course-correct** - Your intent is right, but you've drifted. Here's what to stop/start to realign.

3. **Acknowledge as conscious tradeoff** - You're temporarily off-intent for good reason. Document why and when you expect to return.
```

## When to Use This

- **After monthly-log** - Quick check if this month's work aligned
- **End of quarter** - Bigger picture view of quarterly drift
- **When you feel "off"** - Something feels misaligned but you can't name it
- **Before goal-setting** - Understand if your stated goals match reality
- **Before career conversations** - Know where you stand

## Three Outcomes

After seeing the analysis, you choose:

### 1. Update Intent (Reality is right, intent is stale)
Claude helps you update:
- `foundation/career_intent_FY26.md`
- `foundation/values_and_constraints.md`
- `goals/annual_goals_FY26.md`

**When to choose:** Your work is pulling you in a new direction that feels right. Update your intent to match.

### 2. Course-Correct (Intent is right, work is off)
Claude generates:
- What to stop doing
- What to start doing
- What decisions to reverse
- How to realign

**When to choose:** You want to get back on track with your stated intent.

### 3. Acknowledge Tradeoff (Temporary drift for good reason)
Claude logs this as a conscious exception in `capture/decision_log.md`:
- Why you're off-intent
- How long you expect this to last
- When you plan to return to intent

**When to choose:** You're temporarily drifting (e.g., supporting a critical project) but plan to return to intent.

## Critical Rules

- **NEVER judge drift as good/bad** - It's just data
- Pull work_log data from last 3 months (or specify different range)
- If foundation docs don't exist, tell user: "Can't run drift analysis without foundation. Want to run /career-identity first?"
- Show analysis in full before offering the three options
- Don't assume which option is right - let user choose
- Save analysis to `analysis/drift_analysis_[date].md` for historical tracking

## Tone

- Neutral and data-driven, not judgmental
- Drift is information, not failure
- Assume user is acting with good reasons
- Make all three options feel equally valid
- Help user see patterns they might miss
