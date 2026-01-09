---
description: Conduct monthly work log interview to capture shipped work, impact, and learnings
argument-hint: (no arguments - interactive interview)
---

# Monthly Work Log

This is the **cornerstone workflow** of the Work Operating System. Everything else builds from this monthly capture.

## Usage

- `/monthly-log` - Start interactive monthly work log interview

## What This Does

Conducts a structured 20-30 minute interview to capture:
- What shipped this month
- Impact and outcomes
- Invisible work (what didn't ship but mattered)
- Failures and learnings
- Surprises (good and bad)
- Open threads for next month

After the interview, Claude:
- Formats your responses into a clean monthly entry
- Appends to `capture/work_log.md` with date header
- Auto-extracts potential wins and offers to add them to `capture/wins_ledger.md`
- Offers drift analysis if it seems helpful

## Interview Flow

Claude asks these questions in order:

1. **What shipped this month?** (Projects, features, deliverables)
2. **What was the impact?** (Business metrics, team outcomes, user impact)
3. **What invisible work happened?** (Research, support, mentoring, firefighting)
4. **What failed or didn't work?** (Missed goals, wrong bets, process failures)
5. **What surprised you?** (Unexpected wins, unexpected challenges)
6. **What's carrying forward?** (Open threads, what's in flight for next month)

You can answer in bullet points or conversationally. Claude formats it into the standard structure.

## After Logging

1. Claude scans your responses for potential wins
2. If found, Claude asks: "I noticed these accomplishments. Want me to add them to your wins ledger?"
3. You can accept, decline, or edit before adding
4. Claude may offer: "Want to see drift analysis now?" (compares your work vs stated intent)

## Output Format

Entries are appended to `capture/work_log.md` in this structure:

```markdown
## [Month Year]

### What Shipped
[your response]

### Impact
[your response]

### Invisible Work
[your response]

### Failures & Learnings
[your response]

### Surprises
[your response]

### Open Threads
[your response]
```

## Critical Rules

- **NEVER overwrite existing work_log.md content** - Always append with date header
- Capture responses verbatim - preserve the user's voice and language
- If work_log.md doesn't exist, create it with proper header
- Auto-extract wins conservatively - only obvious accomplishments
- Offer drift analysis after logging, don't force it
- Make this feel like a conversation, not a form

## Tone

- Supportive and curious
- No judgment about failures or gaps
- Celebrate invisible work equally with shipped work
- Make it feel easy, not like homework
