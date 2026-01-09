# Check-In Log

*Anytime reflections - energy, wins, friction, priorities*
*Time estimate: 2-5 minutes*
*Added through: "Do my check-in" command*

---

## Entry Template

```
## [YYYY-MM-DD]

**Energy:** [1-10]

**Wins:**
[Recent accomplishments, things you shipped or improved]

**Friction:**
[What's blocking or draining you]

**What's Next:**
[Your priority for what's coming]

**Notes:**
[Anything else to capture, if relevant]
```

---

## Sample Entries (Quality Spectrum)

### Excellent Entry

```
## 2026-01-03

**Energy:** 6

**Wins:**
- Finished Python automation for subscription data pipeline—now runs daily
- Got positive feedback from VP on executive briefing last week
- Helped Sarah debug a tricky analytics query (she learned something)

**Friction:**
Three meetings that could have been emails. Stakeholder asking for analysis we delivered last month.

**What's Next:**
Set up Slack integration for pipeline alerts. Prep for quarterly review with manager.

**Notes:**
Noticing my best work happens 8-10am before meetings. Should protect that time.
```

### Acceptable Entry

```
## 2026-01-02

**Energy:** 5

**Wins:**
- Submitted report
- Code review feedback given

**Friction:**
Too many meetings again

**What's Next:**
Continue on dashboard work
```

### Minimal Entry (Still Valid)

```
## 2026-01-01

**Energy:** 4

**Wins:**
None this period

**Friction:**
Exhausted from project push

**What's Next:**
Rest and recover
```

---

## Integration Points

Feeds from: Your natural daily work
Feeds into: Monthly work_log (monthly_log workflow extracts entries)
Analyzed by: Claude for energy patterns, recurring friction

Claude will:
- Capture entries conversationally
- Auto-detect patterns (same friction 3+ times = flag)
- Suggest wins for wins_ledger
- Note energy trends for energy_log

---

## Tips

- Energy is just a number 1-10, no explanation needed
- Wins can be anything—shipped code, unblocked team member, learned something
- Friction is important—gets at blockers and sustainability
- Optional notes for anything else
- Don't backfill—forward momentum only
