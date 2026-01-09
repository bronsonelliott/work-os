# Failure Log

*What didn't work - learning orientation, not judgment*
*Time estimate: 2-5 minutes*
*Auto-populated from work_log "What Didn't Work" section*

---

## Entry Template

```
## [Date / Period]

**What Happened:** [What didn't work, what failed, what went wrong]

**Impact:** [What was the consequence?]

**Root Cause:** [Why did this happen? What was in your control?]

**What I Learned:** [Key insight]

**What I'll Do Differently:** [How you'll change behavior/process]

**Status:** [Fixed / Monitoring / Accepted]
```

---

## Sample Entry

```
## January 2026

**What Happened:** First automation attempt failed because vendor API changed without notice

**Impact:** Had to rewrite code, delayed delivery by 1 week

**Root Cause:** 
- Didn't subscribe to vendor changelog (my process gap)
- Vendor didn't communicate changes (their problem)

**What I Learned:** Need better vendor communication process. APIs change, can't assume stability.

**What I'll Do Differently:** 
- Subscribe to all vendor changelogs
- Build in extra time for vendor-dependent work
- Have backup approach if API breaks

**Status:** Fixed - Now monitoring vendor changes

---

## November 2025

**What Happened:** Quarterly planning took 3x longer than expected, missed initial deadline

**Impact:** Delayed Finance team planning, caused scheduling issues

**Root Cause:** Underestimated stakeholder alignment complexity. Didn't scope all participants.

**What I Learned:** Multi-stakeholder planning needs more time upfront for alignment. Can't assume everyone understands the problem.

**What I'll Do Differently:** 
- Budget 2x time for stakeholder alignment
- Do pre-meeting with stakeholders before full group
- Write detailed agenda with time per topic

**Status:** Monitoring - will test new approach next quarter
```

---

## Key Principle

This is NOT about blame or judgment. It's about:
- Understanding what happened
- Learning from it
- Preventing recurrence

---

## Integration Points

Feeds from: work_log (auto-extracted)
Analyzed for: Recurring failures (same issue 2+ times = pattern), root causes
Updates: pattern_recognition.md (when recurring), memory.md
