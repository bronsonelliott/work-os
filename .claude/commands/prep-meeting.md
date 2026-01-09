---
description: Generate meeting prep doc from recent work logs, wins, and goals
argument-hint: "[meeting type/person]" or empty for default 1:1 prep
---

# Meeting Prep

Quick 5-minute automated generation of meeting prep based on your recent work. No input needed—Claude reads your logs and creates talking points.

## Usage

- `/prep-meeting` - Generate prep for manager 1:1 (default)
- `/prep-meeting "1:1 with Sarah"` - Generate prep for specific person
- `/prep-meeting "skip level"` - Generate prep for skip-level meeting

## What This Does

Claude automatically:
1. Reads your most recent `capture/work_log.md` entry
2. Reads recent wins from `capture/wins_ledger.md`
3. Reads your current goals from `goals/annual_goals_FY26.md` and `goals/quarterly_focus.md`
4. Reads recent feedback from `capture/feedback_ledger.md`
5. Synthesizes this into a clean meeting prep doc
6. Saves to `reviews/monthly_1on1_prep.md`
7. Shows you the output for review/editing

## Output Structure

Claude generates:

```markdown
# 1:1 Prep - [Date]

## Current Focus
[From quarterly_focus.md - what you're working on this quarter]

## Recent Impact
[From work_log.md - what shipped, impact, outcomes]

## Wins Worth Highlighting
[From wins_ledger.md - recent accomplishments]

## Blockers/Challenges
[From work_log.md - failures, surprises, open threads]

## Ask/Support Needed
[Synthesized from blockers and open threads]

## Talking Points
- [Key point 1]
- [Key point 2]
- [Key point 3]

## Goal Progress
[From goals - quick status on key goals]
```

## Smart Synthesis

Claude intelligently:
- Prioritizes most recent work (last 30 days)
- Surfaces wins you might forget to mention
- Identifies blockers that need manager support
- Connects your work to stated goals
- Flags if recent feedback is relevant to discussion

## After Generation

1. Claude shows you the generated prep doc
2. You can read it, edit it, or use it as-is
3. Claude asks: "Want me to save this, or make any changes first?"
4. Once saved, you have it ready for your meeting

## When to Use This

**Before manager 1:1s:** Quick reminder of what you've done, what matters, what you need

**Before skip-levels:** Broader view of impact and strategic work

**Before important stakeholder meetings:** Shows your work, wins, and asks

**Before performance reviews:** Quick refresh on recent accomplishments

## Critical Rules

- **NEVER make up work that's not in the logs** - Only synthesize what exists
- Overwrite `reviews/monthly_1on1_prep.md` each time (it's ephemeral prep, not a log)
- If work_log.md is empty/stale, tell user: "Your work log is empty. Want to run /monthly-log first?"
- Focus on last 30 days unless user specifies different timeframe
- Keep it concise - this is a prep doc, not a novel
- If goals files don't exist, generate prep without the goal section

## Tone

- Professional but authentic
- Highlights impact without overselling
- Honest about blockers and needs
- Confident but not arrogant
