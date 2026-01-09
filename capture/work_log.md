# Work Log

*Monthly work capture - the system cornerstone*
*Time estimate: 20-30 minutes*
*Added through: "Run monthly log" command*
*Frequency: Once per month (not daily, not weekly)*

---

## Entry Structure

```
# Monthly Work Log - [Month YYYY]

## What I Shipped / Completed
[Projects, features, analyses, deliverables you finished this month]

## Impact Delivered
[Metrics, decisions influenced, problems solved, people helped]

## Invisible / Undervalued Work
[Mentoring, alignment, cleanup, code refactoring, documentation, process fixes]

## What Didn't Work
[Things that failed, got blocked, or went wrong - just facts, no judgment]

## Surprises or Unexpected Learnings
[What you learned, what was unexpected]

## Open Threads Rolling Into Next Month
[What's still in progress, what carries over]
```

---

## Sample Entry

```
# Monthly Work Log - January 2026

## What I Shipped / Completed
- Delivered Python automation for subscription data pipeline
- Completed quarterly planning with Finance team
- Migrated analytics infrastructure to new cloud provider
- Finished training module for new analysts

## Impact Delivered
- Subscription reporting now runs daily instead of manual weekly (saves 5 hrs/week)
- Quarterly plan caught revenue anomaly worth $50k
- Migration completed 2 weeks ahead of schedule with 0 downtime
- 2 new analysts report feeling confident with onboarding

## Invisible / Undervalued Work
- Mentored Sarah on Python (8 hours across month)
- Documented cloud migration process for future team member
- Refactored legacy analytics code reducing technical debt
- Cleaned up months of old dashboards

## What Didn't Work
- First automation attempt failed due to API changes—had to rewrite
- Quarterly planning took 3x longer than expected due to stakeholder alignment issues
- One analysis delivered late due to data quality problems upstream

## Surprises or Unexpected Learnings
- Learned API was changing—need better vendor communication process
- Discovered Finance team doesn't understand our current reporting—may need education
- Python proficiency improving faster than expected with practice

## Open Threads Rolling Into Next Month
- Cloud migration follow-up tasks (policy updates, security review)
- Sarah's ongoing mentorship continues
- Analyzing why planning took so long—process improvement needed
```

---

## Integration Points

Triggers: Monthly "Run monthly log" workflow
Extracts to: wins_ledger.md (auto-suggests wins to add)
Analyzes for: Goal alignment, energy patterns, recurring failures
Updates: energy_log, pattern_recognition, goals tracking

Claude will:
- Ask about each section conversationally
- Format your responses
- Extract potential wins (auto-suggest)
- Check alignment with quarterly focus goals
- Identify patterns if recurring failures
- Offer drift analysis

---

## Tips

- Forward momentum: Don't backfill if you miss a month, just pick up next month
- Minimum viable: If low activity month, capture that: "Month was light due to [reason]"
- Be honest: "What didn't work" is valuable
- Invisible work matters: Mentoring, cleanup, process improvements—log it
- Open threads: Helps next month be continuous
