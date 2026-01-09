# Cascading Updates - Automatic Sync Rules

This document defines what automatic updates happen when files change. The system stays in sync through these rules.

## Core Principle

When one file updates, you automatically check and apply cascading updates to related files. The user doesn't need to manually update anything—you handle all cross-references.

---

## CAPTURE FILE UPDATE CASCADES

### When capture/check_in_log.md Updated

**Energy Pattern Detection:**
- If energy <4 three consecutive check-ins within 30 days
  → Add entry to `capture/energy_log.md` under "Burnout Signals"
  → Flag to user: "Noticing low-energy pattern over 3 check-ins. Want to talk about it?"

**Friction Pattern Detection:**
- If same friction mentioned 2+ times in 30 days
  → Add to `synthesis/pattern_recognition.md` under "Recurring Friction"
  → Consider suggesting: "Noticing [friction] keeps coming up. What would help address this?"

**Win Extraction Opportunity:**
- If win mentioned in check-in
  → Ask: "That sounds like a win worth adding to your ledger. Should I log it?"
  → If yes → Run add_win workflow

---

### When capture/work_log.md Updated

**Win Extraction:**
- Review "What I Shipped/Completed" and "Impact Delivered" sections
- Identify accomplishments that meet win criteria:
  - Measurable impact
  - Visible to stakeholders
  - Maps to stated goals
- Ask: "I see [X] accomplishments here. Want me to add these to your wins ledger?"
  - If yes → Run add_win workflow for each

**Goal Alignment Check:**
- Compare work_log entries against `goals/quarterly_focus.md`
- Calculate % of work that maps to stated quarterly goals
- If <60% alignment:
  - Flag: "Only X% of your work mapped to your quarterly focus. Want to see what's taking up the rest?"
  - Track this metric in `goals/tracking.md`

**Energy Pattern Extraction:**
- Review work_log for energy mentions ("this drained me", "energizing", "draining")
- If patterns mentioned:
  - Add to `capture/energy_log.md` with context
  - Update energy patterns in `synthesis/pattern_recognition.md`

**Recurring Failure Detection:**
- Compare "What Didn't Work" section to past months
- If same failure type appears 2+ months:
  - Add to `synthesis/pattern_recognition.md` under "Persistent Gaps"
  - Consider asking: "Notice [failure type] came up again. What's blocking you from solving this?"

**Open Threads Tracking:**
- Extract "Open Threads Rolling Into Next Month"
- If threads appear in next month's work_log unchanged:
  - Flag as stalled item
  - Ask: "Notice [thread] has been open 2 months. Still a priority?"

---

### When capture/wins_ledger.md Updated

**Repeated Win Pattern Detection:**
- If same win type appears 3+ times:
  - Add to `synthesis/pattern_recognition.md` under "Repeated Wins"
  - Add to `memory.md` as "Natural Strength: [area]"
  - Note: "You keep winning at [area]. This is a core strength."

**Evidence Quality Check:**
- If win lacks evidence (no metrics, quotes, or links):
  - Ask: "Want to add evidence for this win while it's fresh?"
  - Helps ensure wins can be cited in reviews later

---

### When capture/feedback_log.md Updated

**Recurring Theme Detection:**
- Compare new feedback to all past entries
- If theme appears 3+ times:
  - Add to `synthesis/pattern_recognition.md` under "Recurring Feedback Themes"
  - Add to `memory.md`
  - Flag: "This is the third time you've gotten feedback about [X]. Worth discussing?"

**Career Intent Contradiction Check:**
- Read `foundation/career_intent_FY26.md` for stated strengths
- If feedback contradicts stated strengths:
  - Add to `synthesis/pattern_recognition.md` under "Blind Spots"
  - Flag: "Your manager sees [X] differently than you do. Want to discuss?"

**Action Tracking:**
- 30 days after feedback logged, check `action_taken` field
- If still blank:
  - Ask: "You logged feedback about [X] 30 days ago but no action yet. Want to address or consciously defer?"

---

### When capture/stakeholder_log.md Updated

**Relationship Trend Detection:**
- If stakeholder moves from "Ally" → "Neutral" or "Blocker":
  - Flag: "Relationship with [name] may be shifting. Last contact [date]. Want to proactively address?"

**Sponsor Gap Detection:**
- If no "Sponsor" level relationships documented:
  - Flag: "No executive sponsors documented. This may limit advancement. Want to work on this?"

**Isolation Pattern:**
- If stakeholder_log showing more "Neutral" or "Blocker" than "Ally" or "Sponsor":
  - Flag: "Notice more neutral/blocker relationships. Want to shift dynamics?"

---

### When capture/energy_log.md Updated

**Burnout Signal Detection:**
- If 3+ burnout signals in single quarter:
  - Flag immediately: "Multiple burnout signals this quarter. Want to discuss sustainability?"

**Energy vs Calendar Mismatch:**
- If energy_log shows "X drains me" but calendar shows high allocation to X:
  - Ask: "You said [X] drains you, but I see you spending significant time on it. What's blocking you from saying no?"

---

### When capture/decision_log.md Updated

**Constraint Violation Check:**
- Read `foundation/values_and_constraints.md` constraints section
- Compare new decision against stated constraints
- If decision violates stated constraint:
  - Flag immediately: "You said you wouldn't do [X], but this decision does [X]. Intentional exception or drift?"

**Repeated Constraint Violation:**
- If multiple decisions violate same constraint:
  - Add to `synthesis/pattern_recognition.md`
  - Ask: "You've violated [constraint] three times now. Want to update your constraints or recommit to them?"

**Decision Pattern Tracking:**
- Identify patterns in decisions (always say yes to execs? No to risky projects?):
  - Add to `memory.md` as decision-making pattern
  - Can inform future decision quality

---

## END-OF-PERIOD CASCADES

### End of Month

**Work Log Missing:**
- IF current month has no work_log entry by month end:
  → Gentle nudge (not guilt): "Haven't seen this month's work log yet. Want to run it now, or skip and resume next month?"

**Low Win Activity:**
- IF wins_ledger empty 2+ consecutive months:
  → Ask: "No wins logged in [X] months. Is that accurate, or are you underselling yourself?"

---

### End of Quarter

**Auto-Trigger Synthesis:**
- Automatically run quarterly_synthesis workflow
- Update `synthesis/pattern_recognition.md` with quarter patterns
- Update `synthesis/executive_summary.md` with quarter insights
- Update `memory.md` with quarterly learnings

**Interview Offer:**
- Suggest: "Quarter just ended. Want to run quarterly reflection interview?"
- This updates quarterly_focus for next quarter

**Goal Progress Check:**
- Review `goals/tracking.md`
- Check progress on quarterly goals
- If goal <25% progress at mid-quarter or <50% at end-quarter:
  → Flag: "Goal [X] is behind. Want to adjust expectations or double down?"

**Goal-Work Alignment Check:**
- If quarterly review shows goal-work misalignment:
  → Ask: "Noticed your work didn't align much with quarterly goals. Want to discuss priorities?"

---

### End of Year

**Auto-Trigger Major Synthesis:**
- Automatically run annual_synthesis workflow
- Generate `synthesis/year_at_a_glance.md`
- Update `synthesis/executive_summary.md` with annual summary
- Update `reviews/year_over_year.md` with year-comparison
- Update `memory.md` with annual insights

**Interview Offers:**
- Suggest: "Want to run year-in-review interview?" (if not already done)
- Suggest: "Want to upload any past performance reviews for pattern extraction?"

**Goal Achievement Assessment:**
- Review FY26 goals against actual year
- Generate summary of achievement
- Note what exceeded, what missed, why

**Career Progress Assessment:**
- Review career_target_3yr.md against actual year progress
- Assess if on track for 3-year targets
- Update tracking in career_target_3yr.md

---

## UPLOAD DOCUMENT CASCADES

### When upload Processed

**Auto-Execute Extract Pattern Workflow:**
- Automatically run extract_patterns_from_upload
- Update `uploads/document_synthesis.md` with extraction log
- Update `uploads/pattern_summary.md` with patterns

**Multi-Document Pattern Synthesis:**
- If 3+ documents uploaded and synthesized:
  - Look for patterns across all documents
  - Update `uploads/pattern_summary.md` with multi-year trends
  - Update `memory.md` with longitudinal insights

**Pattern vs Self-Perception Check:**
- Compare extracted patterns to user's self-perception (from memory.md or foundation/)
- Flag any significant misalignments
- Add to `synthesis/pattern_recognition.md` under "Blind Spots"

---

## SYNTHESIS FILE CASCADES

### When synthesis/pattern_recognition.md Updated

**Major Pattern Detection:**
- When pattern appears 3+ times:
  - Automatically add to `memory.md`
  - Consider if this should influence recommendations

**Blind Spot Identification:**
- When self-perception vs feedback misalignment detected:
  - Add to `memory.md`
  - Flag to user: "Potential blind spot: [description]"

---

### When memory.md Updated

**Career Trajectory Assessment:**
- Review memory.md for career patterns
- If patterns suggest career stagnation or plateau:
  - Flag: "Noticing pattern [X]. Worth discussing career direction?"

**Decision-Making Pattern:**
- If decision pattern emerges (always yes to execs, avoids risk, etc.):
  - Note in memory.md
  - Can inform future decision guidance

---

## INTERVIEW COMPLETION CASCADES

### After Any Interview Completed

**File Cross-Reference Updates:**
- Review all files that reference updated foundation documents
- Ensure consistency across system
- Example: If career_intent updated in interview, ensure goals/annual_goals_FY26.md still aligns

**Pattern Checks:**
- Interview responses often reveal patterns
- Add new patterns to `memory.md`
- Update `synthesis/pattern_recognition.md` if patterns detected

---

## DRIFT ANALYSIS CASCADES

### When Drift Analysis Runs

**If User Chooses Course Correction:**
- Ask: "What specific changes will you make?"
- Log decisions in `capture/decision_log.md`
- Add to `memory.md` as "conscious recommitment to [constraint]"

**If User Updates Intent:**
- Run relevant interview to update foundation documents
- Execute all cascades for interview completion
- Update `memory.md` with intent shift

**If User Acknowledges Drift:**
- Log in `memory.md` as "conscious tradeoff"
- Note which constraints/intents user is deprioritizing
- Can inform future drift analysis

---

## CASCADING UPDATE EXECUTION CHECKLIST

When executing cascades, follow this pattern:

1. **Detect trigger** (file update, end of period, workflow completion)
2. **Identify cascade rules** applicable to this trigger
3. **Read necessary source files** to make update decision
4. **Execute update** if criteria met
5. **Show user** what was updated and why
6. **Continue system operation** (don't get stuck in cascade loop)

---

## Anti-Patterns in Cascading Updates

❌ Update files without telling user (always inform of cascades)
❌ Let cascades go unexecuted (they're essential to system integrity)
❌ Update old data with new patterns without context (always note source)
❌ Require user action for cascade (cascades are automatic)
❌ Over-synthesize (don't force patterns where data unclear)

✅ Execute cascades automatically
✅ Tell user what cascaded and why
✅ Keep all files in sync
✅ Flag patterns only when criteria met
✅ Update memory.md regularly
✅ Synthesize quarterly and annually

---

## Cascade Frequency Summary

**With Every Capture Update:**
- Pattern detection (2+ or 3+ occurrences)
- Alignment checks (goal, constraint, intent)
- Evidence quality checks
- Relationship trend detection

**At Month End:**
- Missing work_log nudges
- Win activity checks

**At Quarter End:**
- Synthesis (auto-trigger quarterly_synthesis)
- Goal progress check
- Interview offer

**At Year End:**
- Major synthesis (auto-trigger annual_synthesis)
- Year comparison
- Multi-year pattern analysis
- Interview offers
- Upload processing offer

**Continuous:**
- Constraint violation detection (immediate)
- Burnout signal detection (immediate)
- Blind spot flagging (when detected)
- Memory.md updates (whenever patterns emerge)
