# Workflow Definitions - Executable Operations

This document defines every workflow that Claude Code executes. Each workflow includes trigger conditions, step-by-step execution, file I/O operations, and cascading updates.

---

## CAPTURE WORKFLOWS

These workflows capture user input through conversation and write structured entries to capture/ files.

### check_in

**Trigger:** User says any variation of "check in", "do my check-in", "quick check in", "check in today"

**Time Estimate:** 2-5 minutes

**Execution:**

1. Greet: "Let's do a quick check-in."
2. Ask Question 1: "What's your energy level right now, 1-10?"
   - Capture response (just the number or number + brief context)
3. Ask Question 2: "What wins are worth remembering from the past few days?"
   - Capture response (can be bullet points or conversational)
4. Ask Question 3: "Any friction points or blockers?"
   - Capture response
5. Ask Question 4: "What's your priority for what's next?"
   - Capture response
6. Ask Question 5 (optional): "Anything else to note?"
   - Capture if provided, skip if user says no

7. Format entry with timestamp:
```
## [YYYY-MM-DD]

**Energy:** [1-10]

**Wins:**
[formatted response from Q2]

**Friction:**
[formatted response from Q3]

**What's Next:**
[formatted response from Q4]

**Notes:**
[optional response from Q5]
```

8. Append to `capture/check_in_log.md`

9. Execute cascading updates (see system/cascading_updates.md):
   - If energy <4: Note in energy_log burnout signal
   - If same friction mentioned 2+ times in 30 days: Add to pattern_recognition
   - If win mentioned: Ask "Should I add this to your wins ledger?"

10. Confirm: "Check-in logged. [mention pattern if detected, e.g., 'Notice third low-energy check-in in a row.']"

---

### monthly_log

**Trigger:** "Run monthly log", "Do my monthly log", "Monthly work log", "Log this month"

**Time Estimate:** 20-30 minutes

**Execution:**

1. Greet: "Let's capture this month's work. I'll walk you through it, then generate a formatted entry."

2. Ask Q1: "What did you ship or complete this month? Projects, features, analyses—anything you finished."
   - Capture response (can be bullet points, conversational, mixed)

3. Ask Q2: "What impact did this work have? Think metrics, decisions influenced, problems solved, people helped."
   - Capture response

4. Ask Q3: "What invisible or undervalued work did you do? Mentoring, alignment, cleanup, code refactoring, documentation, process fixes—things that matter but don't get visibility."
   - Capture response

5. Ask Q4: "What didn't work this month? Things that failed, got blocked, or went wrong. Just facts, no judgment."
   - Capture response
   - NOTE: Check if similar to past months → flag for recurring failure pattern

6. Ask Q5: "Any surprises or unexpected learnings?"
   - Capture response

7. Ask Q6: "What's rolling into next month that's still open?"
   - Capture response

8. Format entry:
```
# Monthly Work Log - [Month YYYY]

**What I Shipped / Completed**
[formatted Q1]

**Impact Delivered**
[formatted Q2]

**Invisible / Undervalued Work**
[formatted Q3]

**What Didn't Work**
[formatted Q4]

**Surprises or Unexpected Learnings**
[formatted Q5]

**Open Threads Rolling Into Next Month**
[formatted Q6]
```

9. Append to `capture/work_log.md`

10. Execute cascading updates:
    - Extract potential wins from "shipped" and "impact" sections
    - Ask: "I see [X] accomplishments. Should I add these to your wins ledger?"
    - If yes → Run add_win workflow for each
    - Check alignment: Compare work to `goals/quarterly_focus.md`
    - If <60% alignment with quarterly goals → Flag: "Only X% of your work mapped to Q focus. Want to see what's taking up the rest?"
    - Extract energy patterns from response 5
    - Check for recurring failures (same issue type 2+ months)
    - Update `synthesis/pattern_recognition.md` if patterns found

11. Offer drift check: "Based on everything so far, want me to tell you what you're underweight on vs overweight on?"
    - If yes → Run drift_analysis

12. Confirm: "Monthly log complete. Updated [files]. Next check-in: [encourage anytime, no schedule]"

---

### add_win

**Trigger:** "Log this win", "Add a win", "Win to log", used also by monthly_log when extracting wins

**Time Estimate:** 3-5 minutes

**Execution:**

1. Ask Q1: "What's the win? What did you accomplish? Be specific."
   - Capture response

2. Ask Q2: "Why did it matter? What impact, value, or benefit did it create?"
   - Capture response

3. Ask Q3: "Who benefited or cares about this?"
   - Capture response

4. Ask Q4: "What's the evidence? Metrics, quotes, links, before/afters?"
   - Capture response (can be none if not available yet)

5. Format entry:
```
## [Accomplishment Title]

**What:** [Q1 response]

**Why It Mattered:** [Q2 response]

**Who Benefited:** [Q3 response]

**Evidence:**
[Q4 response or "TBD - will update when available"]
```

6. Append to `capture/wins_ledger.md`

7. Execute cascading updates:
   - If this is 3rd win of similar type → Add to pattern_recognition as "natural strength"
   - Update memory.md if pattern emerges

8. Confirm: "Win logged. [mention pattern if detected]"

---

### add_feedback

**Trigger:** "Log this feedback", "Add feedback", "Feedback to log"

**Time Estimate:** 2-3 minutes

**Execution:**

1. Ask Q1: "What was the feedback? Quote it if possible—I want exact wording."
   - Capture response (verbatim preferred)

2. Ask Q2: "Who gave it and what was the context? When, where, why?"
   - Capture response

3. Ask Q3: "Your interpretation—what did they mean? What's your take?"
   - Capture response

4. Ask Q4 (optional): "Any action you took or plan to take based on this?"
   - Capture if provided

5. Format entry:
```
## [Date]

**Feedback:** "[exact quote if possible, otherwise paraphrase]"

**Source:** [who, context, date]

**My Interpretation:** [Q3 response]

**Action Taken/Planned:** [Q4 response or "None yet"]
```

6. Append to `capture/feedback_log.md`

7. Execute cascading updates:
   - Check for recurring themes (same feedback 3+ times)
   - Check against `foundation/career_intent_FY26.md` → Flag if contradicts stated strengths
   - If no action_taken yet, 30 days later: Nudge "You logged feedback about [X] but no action. Want to address or consciously defer?"
   - Update memory.md if recurring theme emerges

8. Confirm: "Feedback logged. [mention pattern if detected]"

---

### add_decision

**Trigger:** "Log this decision", "Decision to log", "Add decision"

**Time Estimate:** 2-3 minutes

**Execution:**

1. Ask Q1: "What did you decide? What did you say yes/no to?"
   - Capture response

2. Ask Q2: "Why did you decide that? What were your reasons?"
   - Capture response

3. Ask Q3: "What are you trading? What did you give up by choosing this?"
   - Capture response

4. Ask Q4 (optional): "Any regrets or second thoughts?"
   - Capture if provided

5. Format entry:
```
## [Date]

**Decision:** [Q1 response]

**Reasoning:** [Q2 response]

**Tradeoff:** [Q3 response]

**Reflections:** [Q4 response or "None yet"]
```

6. Append to `capture/decision_log.md`

7. Execute cascading updates:
   - Check against `foundation/values_and_constraints.md` constraints
   - If decision violates stated constraint → Flag: "You said you wouldn't [X], but this decision does [X]. Intentional exception or drift?"
   - If multiple decisions violate same constraint → Add to pattern_recognition
   - Update memory.md with decision patterns

8. Confirm: "Decision logged. [mention constraint check if relevant]"

---

## INTERVIEW WORKFLOWS

These workflows conduct structured interviews, capture responses, and synthesize into files.

### career_identity_interview

**Trigger:** "Run career identity interview", "Career identity interview", "Career interview"

**Time Estimate:** 20-30 minutes

**Execution:**

1. Tell user: "I'm running the career identity interview—12 questions about who you are professionally. Answer conversationally. I'll turn your responses into structured documents after."

2. Load `interviews/career_identity.md` → Get question list

3. Ask each question one at a time (with optional follow-ups if response is brief):
   - "What kind of professional are you? Not your title—your identity."
   - "What work feels like play to you? When do you lose track of time?"
   - "What work feels like punishment? What drains you?"
   - "What do you want to be known for in 10 years?"
   - "What do you NOT want to be known for?"
   - "How do you define success at work?"
   - "What does 'enough' look like for you?"
   - "What are you willing to trade for advancement?"
   - "What are you NOT willing to trade?"
   - "What would make you walk away?"
   - "What constraints are you working within?"
   - "What would your ideal role look like?"

4. Capture all responses in user's own words

5. Synthesize responses into target documents:
   - `foundation/values_and_constraints.md` → Fill sections: Core Values, Lines I Will Not Cross, What "Enough" Looks Like
   - `foundation/career_intent_FY26.md` → Fill sections: What I Am Optimizing For, Explicit Tradeoffs, Constraints
   - `foundation/principles.md` → Fill sections: How I Define Success, My Relationship With Work
   - `memory.md` → Add key insights about career identity

6. Generate these files with populated responses

7. Show user all generated documents: "Here's what I captured from our conversation."

8. Ask: "Want to edit anything before I save?"
   - If edits requested → Apply edits
   - Confirm edits

9. Save all files

10. Execute cascading updates:
    - Update memory.md with career identity insights

11. Confirm: "Career identity documents complete. Your foundation is set. Ready to set goals next?"

---

### goal_setting_interview

**Trigger:** "Run goal setting interview", "Goal setting", "Set my goals"

**Time Estimate:** 20-30 minutes

**Execution:**

1. Tell user: "I'm running the goal-setting interview—10 questions about what you want to achieve. Answer honestly, including what you're really optimizing for (not just official goals). I'll turn this into your goal documents."

2. Load `interviews/goal_setting.md` → Get question list

3. Ask each question:
   - "What are your official goals for this year? What did your company/manager ask you to achieve?"
   - "Why do these goals exist—what's your real motivation?"
   - "What does success actually look like for each goal?"
   - "How will others SEE that you succeeded? Observable signals?"
   - "What are you really optimizing for that isn't in official goals?" [Shadow goals]
   - "What are you explicitly NOT doing this year?"
   - "What tradeoffs are you making? What will you sacrifice?"
   - "What constraints are you working within?"
   - "What would make this year feel successful?"
   - "What would make this year feel like failure?"

4. Capture all responses

5. Synthesize into target documents:
   - `goals/annual_goals_FY26.md` → Fill: Declared Goals, Shadow Goals, Success Definition
   - `foundation/career_intent_FY26.md` → Fill: Career Intent, Tradeoffs, Constraints
   - `goals/quarterly_focus.md` (Q1) → Derive top 3 priorities from annual goals
   - `memory.md` → Add what user really cares about

6. Generate documents with populated responses

7. Show user: "Here's your goals for FY26."

8. Ask: "Want to edit anything?"
   - Apply edits if requested

9. Save all files

10. Execute cascading updates:
    - Update memory.md

11. Confirm: "Goals set for FY26. Quarterly focus set for Q1. Ready to start using the system."

---

### year_in_review_interview

**Trigger:** "Run year in review", "Year in review interview", "Annual review interview"

**Time Estimate:** 30-45 minutes

**Execution:**

1. Tell user: "Year-in-review interview—15 questions reflecting on the past year. Answer conversationally. I'll turn this into your year-end review and synthesis."

2. Load `interviews/year_in_review.md` → Get question list

3. Ask each question:
   - "Highlights first—what are you most proud of?"
   - "What are you proud of that no one else sees?"
   - "What surprised you about your own performance?"
   - "Where did you underdeliver and why?"
   - "What drained you the most?"
   - "What energized you?"
   - "Where did you avoid hard decisions?"
   - "What feedback landed this year?"
   - "What feedback didn't land?"
   - "What would you not repeat?"
   - "If this year repeated 10 times, would you be satisfied?"
   - "What did you learn about yourself?"
   - "What would you tell yourself 12 months ago?"
   - "What's unfinished that matters?"
   - "What are you letting go of?"

4. Capture all responses

5. Synthesize into target documents:
   - `reviews/year_end_review.md` → Fill: Summary, Key Wins, Misses, Growth, Feedback Themes, Next Focus
   - `synthesis/year_at_a_glance.md` → Create narrative arc of year from all responses
   - `synthesis/pattern_recognition.md` → Update all sections based on year data
   - `memory.md` → Add year insights

6. Generate documents

7. Offer: "Want me to ask follow-up questions on any specific areas? I can go deeper on highlights, challenges, feedback, or learnings."
   - If yes → Ask follow-ups
   - Synthesize follow-ups into documents

8. Show user generated documents

9. Ask: "Want to edit anything?"
   - Apply edits

10. Save all files

11. Execute cascading updates:
    - Update synthesis/ documents
    - Update memory.md

12. Confirm: "Year-end review complete. [key insights noted]"

---

### quarterly_reflection_interview

**Trigger:** "Run quarterly reflection", "Q[X] reflection", "Quarter reflection"

**Time Estimate:** 15-20 minutes

**Execution:**

1. Tell user: "Quarter reflection interview—10 questions about how the quarter went. I'll update your quarterly patterns and next quarter's focus."

2. Load `interviews/quarterly_reflection.md` → Get question list

3. Ask each question:
   - "What actually moved forward this quarter?"
   - "What felt busy but didn't matter?"
   - "Where did you over-rotate?"
   - "Where did you under-invest?"
   - "What surprised you?"
   - "What are you avoiding?"
   - "What needs to change next quarter?"
   - "What should you stop doing?"
   - "What energy patterns emerged?"
   - "What stakeholder signals did you notice?"

4. Capture all responses

5. Synthesize into target documents:
   - `goals/quarterly_focus.md` (next quarter) → Fill: Top 3 Priorities, De-Priorities, Win Definition
   - `synthesis/pattern_recognition.md` → Update all sections from quarterly data
   - `capture/energy_log.md` → Add patterns from energy question
   - `memory.md` → Add quarterly insights

6. Generate documents

7. Show user: "Here's your Q[X+1] focus and quarterly patterns."

8. Ask: "Want to edit?"
   - Apply edits

9. Save all files

10. Execute cascading updates:
    - Update all synthesis files
    - Update memory.md

11. Confirm: "Quarterly reflection complete. Q[X+1] focus set."

---

### manager_relationship_interview

**Trigger:** "Run manager relationship interview", "Manager interview", "Manager relationship"

**Time Estimate:** 15 minutes

**Execution:**

1. Tell user: "Manager relationship interview—10 questions about your relationship with your manager. I'll update your role expectations and stakeholder tracking."

2. Load `interviews/manager_relationship.md` → Get question list

3. Ask each question (tailored to manager relationship understanding)

4. Capture all responses

5. Synthesize into target documents:
   - `foundation/role_expectations.md` → Fill: Official Expectations, Actual Expectations, Manager Perspective
   - `capture/stakeholder_log.md` → Add/update manager entry with trust signals
   - `memory.md` → Add manager dynamic insights

6. Generate documents

7. Show user: "Here's your updated role expectations and manager relationship profile."

8. Ask: "Want to edit?"
   - Apply edits

9. Save all files

10. Execute cascading updates:
    - Update memory.md

11. Confirm: "Manager relationship documented."

---

## OUTPUT WORKFLOWS

These workflows read files and generate outputs (no user input capture, just generation + show).

### prep_1on1

**Trigger:** "Prep me for my 1:1", "Prep 1:1 with [manager name]", "1:1 prep", "Meeting prep"

**Time Estimate:** 5 minutes (instant generation)

**Execution:**

1. Read source files:
   - `capture/work_log.md` (most recent month)
   - `capture/wins_ledger.md` (recent entries, past 2 months)
   - `goals/quarterly_focus.md` (current priorities)
   - `capture/feedback_log.md` (entries from past month)
   - `capture/stakeholder_log.md` (manager entry if exists)

2. Generate `reviews/monthly_1on1_prep.md` with sections:
```
# Monthly 1:1 Prep - [Month Year]

## What I've Focused On This Month
[from work_log "shipped/completed"]

## Impact I've Delivered
[from work_log "impact" + wins_ledger recent entries]

## Blockers / Risks / Concerns
[from work_log "what didn't work" + check_in friction points]

## Priorities For Next Month
[from quarterly_focus + work_log "open threads"]

## Asks / Support Needed
[synthesized from blockers or ask user]
```

3. Show user the generated document

4. Ask: "This is what I pulled together. Want to add anything or edit before your meeting?"
   - If edits → Apply edits and show updated version
   - If no edits → Confirm ready

5. Confirm: "Your 1:1 prep is ready. Good luck in your meeting."

---

### generate_mid_year_review

**Trigger:** "Generate my mid-year review", "Mid-year review", "Mid-year self-assessment"

**Time Estimate:** 10-15 minutes (generation + review)

**Execution:**

1. Read source files:
   - `capture/work_log.md` (Jan-June entries)
   - `capture/wins_ledger.md` (all entries Jan-June)
   - `goals/annual_goals_FY26.md` (reference targets)
   - `capture/feedback_log.md` (all entries Jan-June)
   - `goals/tracking.md` (if exists, check progress)

2. Generate `reviews/mid_year_review.md`:
```
# Mid-Year Review - FY26

## Overall Summary
[2-3 paragraph narrative of first half]

## Focus Areas (What I Said I'd Do)
[from annual goals]

## Key Wins & Impact
[from wins_ledger with evidence]

## Progress on Goals
[goal-by-goal assessment based on work_log]

## Feedback Themes
[recurring themes from feedback_log]

## What I'm Underweight / Overweight On
[from work_log analysis vs goals]

## Next Half Focus
[recommendations for H2]
```

3. Show user: "Here's your mid-year review based on your logs."

4. Ask: "Want to edit or add anything?"
   - Apply edits

5. Confirm: "Mid-year review complete."

---

### generate_year_end_review

**Trigger:** "Generate my year-end review", "Year-end review", "Annual self-assessment"

**Time Estimate:** 15-30 minutes (generation + review)

**Execution:**

1. Offer: "Want to run the year-in-review interview first, or should I generate from your logs?"
   - If interview → Run year_in_review_interview first
   - If logs only → Continue below

2. Read source files:
   - Entire `capture/work_log.md` (all months)
   - Entire `capture/wins_ledger.md`
   - Entire `capture/feedback_log.md`
   - `goals/annual_goals_FY26.md` (reference)
   - `reviews/mid_year_review.md` (if exists, for continuity)

3. Generate `reviews/year_end_review.md`:
```
# Year-End Review - FY26

## Executive Summary
[1-2 paragraph year overview]

## Goals & Progress
[FY26 goals vs actual achievement]

## Key Wins
[major accomplishments from wins_ledger]

## Impact Delivered
[aggregate impact from work_log]

## Feedback Themes
[recurring themes across entire year]

## Growth & Learning
[what you learned about yourself]

## What I Did Well
[strengths demonstrated through year]

## What I Could Improve
[development areas from feedback + self-reflection]

## Next Year Focus
[recommendations for FY27]
```

4. Show user: "Here's your year-end review based on your full year of logs."

5. Ask: "Want to edit or add context?"
   - Apply edits

6. Execute cascading updates:
   - Update `synthesis/year_at_a_glance.md` if not already done
   - Update `memory.md` with year insights

7. Confirm: "Year-end review complete."

---

## ANALYSIS WORKFLOWS

These workflows analyze existing data and surface insights.

### drift_analysis

**Trigger:** "Where am I drifting?", "Show me drift", "Am I drifting?", or triggered by monthly_log

**Time Estimate:** 10 minutes

**Execution:**

1. Read source files:
   - `foundation/career_intent_FY26.md` (stated intent)
   - `foundation/values_and_constraints.md` (stated constraints)
   - `capture/work_log.md` (past 3 months)
   - `capture/decision_log.md` (past 3 months)
   - `capture/energy_log.md` (patterns)
   - `goals/annual_goals_FY26.md` (declared + shadow)
   - `capture/check_in_log.md` (recent entries for general sense)

2. Analyze misalignments:
   - Compare stated career_intent vs actual work patterns
   - Compare stated constraints vs decision_log instances
   - Compare declared goals % of time vs shadow goals % of time
   - Compare stated energy drains vs calendar allocation

3. Generate drift analysis:
```
# Drift Analysis - [Date]

## Intent vs Reality
You said: [quote from career_intent]
Reality: [pattern from work_logs from past 3 months]
Gap: [specific misalignment with example]

## Constraint Violations
You said you wouldn't: [constraint from values_and_constraints]
But decision log shows: [specific instances]

## Goal Allocation
Official goals: [X]% of time
Shadow goals: [Y]% of time
[comment on balance]

## Energy Mismatch
[if applicable]: You said [X] drains you, but calendar shows [Y]% allocation to [X]

## What This Means
[brief interpretation of patterns]

## Options
Option 1: Update your stated intent to match reality
Option 2: Course-correct your behavior to match stated intent
Option 3: Acknowledge the drift as conscious tradeoff
```

4. Show user the drift analysis

5. Ask: "What would help most—updating your intent, course-correcting, or discussing this?"
   - If update intent → Offer relevant interview (career_identity_interview, goal_setting_interview)
   - If course-correct → Ask what specific changes they'll make, log in decision_log
   - If acknowledge → Note in memory.md as conscious tradeoff

6. Confirm with action plan

---

### quarterly_synthesis (Auto-Triggered)

**Trigger:** End of quarter (manual or automatic based on date check)

**Time Estimate:** Automatic (10-15 min when run)

**Execution:**

1. Read all files from past quarter:
   - All capture/ files
   - All feedback_log, stakeholder_log entries
   - All decision_log entries
   - Work_log entries

2. Extract patterns:
   - Most frequent feedback themes
   - Most repeated win types (natural strengths)
   - Most persistent gaps
   - Energy patterns (what drained/energized)
   - Stakeholder relationship patterns
   - Decision pattern themes

3. Update `synthesis/pattern_recognition.md`:
   - Recurring Feedback Themes: [with frequency and examples]
   - Repeated Wins: [natural strengths shown by repeated win types]
   - Persistent Gaps: [things still showing up]
   - Energy Patterns: [what drained, what energized]
   - Stakeholder Patterns: [relationship trends]
   - Decision Patterns: [yes/no decision themes]

4. Update `synthesis/executive_summary.md`:
   - Add quarter insights
   - Note major patterns
   - Link to quarterly focus
   - Identify next quarter priorities

5. Update `memory.md`:
   - Add emerging patterns
   - Note career trajectory signals
   - Add insights about how user works

6. Tell user: "Just ran quarterly synthesis. Found [X] key patterns:
   - [pattern 1]
   - [pattern 2]
   - [pattern 3]

Want to see the full synthesis?"

7. If yes → Show relevant sections of pattern_recognition.md

---

### annual_synthesis (Auto-Triggered at Year End)

**Trigger:** End of year

**Time Estimate:** Automatic (15-20 min when run)

**Execution:**

1. Read entire year of data from all capture/ files

2. Generate `synthesis/year_at_a_glance.md`:
   - Narrative arc of the year
   - Quarterly themes and progression
   - Major wins across all quarters
   - Key learnings and growth
   - How the year changed you
   - What matters most looking back

3. Update `synthesis/executive_summary.md`:
   - Add year summary
   - Note year-long patterns
   - Career trajectory assessment
   - Key insights about user

4. Update `reviews/year_over_year.md` (if prior years exist):
   - Compare this year to past years
   - Identify progression
   - Note what's different

5. Update `memory.md`:
   - Add year insights
   - Note career patterns
   - Add wisdom from year

6. Tell user: "Generated year-end synthesis. Key insights:
   - [insight 1]
   - [insight 2]
   - [insight 3]

Want to see the full year-at-a-glance narrative?"

---

## UPLOAD WORKFLOWS

### extract_patterns_from_upload (Automated)

**Trigger:** User uploads document and says "Extract patterns", "Synthesize this", "Analyze this review"

**Time Estimate:** 5-10 minutes (automated)

**Execution:**

1. Read uploaded document (PDF, markdown, text, or image)

2. Extract:
   - Strengths mentioned (specific phrases and themes)
   - Development areas mentioned
   - Specific feedback quotes
   - Performance rating/level if present
   - Compensation changes if mentioned
   - Promotion signals or advancement indicators
   - Manager comments or tone

3. Create entry in `uploads/document_synthesis.md`:
```
## [Document Name / Review Title]
Uploaded: [date]
Type: [Performance Review / 360 Feedback / Letter / Notes]
Source: [where it's from]

**Key Themes Extracted:**
- [theme 1 with quote if applicable]
- [theme 2]
- [theme 3]

**Where Incorporated:**
- Added to pattern_summary.md under [category]
- Added to memory.md: [insight]
```

4. Update `uploads/pattern_summary.md`:
   - Add to "Repeated Strengths" if theme already in summary
   - Add to "Persistent Development Areas" if recurring
   - Add to "Blind Spots" if self-perception misaligned
   - Add to "Career Trajectory Signals" if advancement-related
   - Add to "Compensation Signals" if money-related

5. Update `memory.md`:
   - Add key insights about user from document
   - Note if patterns align/conflict with self-perception
   - Add to career understanding

6. Check if quarterly synthesis due → Update `synthesis/executive_summary.md` if yes

7. Tell user: "Extracted patterns from [document name]. Found [X] themes:
   - [theme 1]
   - [theme 2]
   - [theme 3]

[Note on recurring patterns if applicable]. Want to see the full pattern analysis?"

8. If yes → Show relevant sections of pattern_summary.md

---

## SYNTHESIS EXECUTION (End-of-Period Auto-Triggers)

### End of Month
- IF work_log not updated: Gentle nudge "Haven't seen this month's work log yet. Want to run it now?"
- IF wins_ledger empty 2+ months: "No wins logged in 2 months. Is that accurate, or are you underselling yourself?"

### End of Quarter
- AUTO-RUN quarterly_synthesis
- Offer: "Quarter just ended. Want to run quarterly reflection interview?"

### End of Year
- AUTO-RUN annual_synthesis
- Offer: "Want to run year-in-review interview?" (if not already done)
- Offer: "Want to upload any past performance reviews for pattern extraction?"

---

## Workflow Error Handling

### Ambiguous User Request
→ Ask clarifying question: "To help you best, could you clarify what you need?"

### User Hasn't Updated in Weeks/Months
→ Don't guilt them. Offer: "Want to help you restart? No backfilling needed—just pick up forward."

### No Data Yet (New User)
→ Suggest: "Start with career identity interview to set foundation, then goal setting interview for FY26 goals."

### Synthesis Finds No Clear Pattern
→ Tell honestly: "Not enough data yet to spot clear patterns. Come back after a few more entries."

### File Write Fails
→ Tell user: "Had trouble writing to [file]. Can you check file permissions?"

### Cascade Triggers Concern
→ Flag to user: "Noticed [X]. Want to discuss?"

---

## Workflow Summary Quick Reference

**Capture (User Input):**
- check_in (2-5 min) → check_in_log.md
- monthly_log (20-30 min) → work_log.md
- add_win (3-5 min) → wins_ledger.md
- add_feedback (2-3 min) → feedback_log.md
- add_decision (2-3 min) → decision_log.md

**Interview (Structured Conversations):**
- career_identity_interview (20-30 min) → foundation/ files
- goal_setting_interview (20-30 min) → goals/ + foundation/
- year_in_review_interview (30-45 min) → reviews/ + synthesis/
- quarterly_reflection_interview (15-20 min) → goals/ + synthesis/
- manager_relationship_interview (15 min) → foundation/ + capture/

**Output (Generation):**
- prep_1on1 (5 min) → reviews/monthly_1on1_prep.md
- generate_mid_year_review (10-15 min) → reviews/mid_year_review.md
- generate_year_end_review (15-30 min) → reviews/year_end_review.md

**Analysis:**
- drift_analysis (10 min) → analysis + recommendations

**Synthesis:**
- quarterly_synthesis (auto) → synthesis/ files
- annual_synthesis (auto) → synthesis/ files

**Upload:**
- extract_patterns_from_upload (auto) → uploads/ + synthesis/
