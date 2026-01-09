# Work Operating System - Commands Reference

This is your guide to interacting with the Work Operating System through Claude Code. You use natural language—not exact commands.

All interactions happen by talking to Claude. You don't manually edit files.

## Two Ways to Interact

**Natural Language (Primary):**
- "Do my check-in"
- "Run monthly log"
- "Prep me for my 1:1"
- "Where am I drifting?"

**Slash Commands (Quick Access):**
- `/check-in` - Quick 2-5 min check-in
- `/monthly-log` - Monthly work log interview
- `/log-win [description]` - Log accomplishment
- `/log-feedback` - Log feedback
- `/log-decision [description]` - Log decision with constraint checking
- `/prep-meeting [optional: person/type]` - Generate meeting prep
- `/drift-analysis` - Compare intent vs reality
- `/goal-progress` - Check progress against goals
- `/quarterly-reflection [optional: quarter]` - End-of-quarter reflection

Both approaches work identically - use whichever feels more natural.

---

## CAPTURE COMMANDS

These capture your work, feedback, wins, and decisions.

### Check-In (Anytime, 2-5 min)
**Say:** "Do my check-in" / "Check in" / "Quick check in"

What happens:
- Claude asks: Energy level? Wins? Friction? What's next?
- You answer conversationally
- Claude logs to check_in_log.md
- If patterns detected, Claude mentions them

**Good for:** Anytime quick reflection, tracking energy, capturing quick wins

---

### Monthly Work Log (Once per month, 20-30 min)
**Say:** "Run monthly log" / "Do my monthly log" / "Monthly work log"

What happens:
- Claude asks: What shipped? Impact? Invisible work? Failures? Surprises? Open threads?
- You answer conversationally (bullet points fine)
- Claude formats and logs to work_log.md
- Claude auto-extracts potential wins and asks if you want to add them
- Claude offers drift analysis if helpful

**Good for:** Monthly capture of work, impact, and learnings

**Note:** This is the cornerstone. Everything else builds from this.

---

### Log a Win (3-5 min)
**Say:** "Log this win" / "Add a win" / "Win to log"

What happens:
- Claude asks: What? Why it mattered? Who benefited? Evidence?
- You answer
- Claude logs to wins_ledger.md
- Claude checks for repeated win patterns

**Good for:** Adding accomplishments you don't want to forget

**Used by:** monthly_log (auto-extracts wins), before 1:1s (to remind yourself), review prep

---

### Log Feedback (2-3 min)
**Say:** "Log this feedback" / "Add feedback" / "Feedback to log"

What happens:
- Claude asks: Exact wording? Who, when, context? Your interpretation? Action?
- You answer
- Claude logs to feedback_log.md verbatim
- Claude checks for patterns (same feedback 3x = pattern)

**Good for:** Capturing feedback while fresh, building evidence for patterns

**Note:** Claude prefers exact quotes over paraphrasing

---

### Log a Decision (2-3 min)
**Say:** "Log this decision" / "Decision to log" / "Add decision"

What happens:
- Claude asks: What did you decide? Why? What tradeoff? Regrets?
- You answer
- Claude logs to decision_log.md
- Claude checks against your constraints

**Good for:** Tracking what you're saying yes/no to, understanding decision patterns

**Note:** Claude will flag constraint violations if relevant

---

## INTERVIEW COMMANDS

These conduct structured interviews that populate your foundation documents.

### Career Identity Interview (20-30 min, do once or re-run when direction shifts)
**Say:** "Run career identity interview" / "Career identity interview" / "Career interview"

What happens:
- Claude asks 12 questions about who you are professionally
- You answer conversationally
- Claude populates foundation/values_and_constraints.md, foundation/career_intent_FY26.md, foundation/principles.md
- Claude shows you what was generated
- You can edit before Claude saves

**Good for:** Setting your foundation (do first), resetting when direction changes

**Output:** Your core values, constraints, definition of success

---

### Goal-Setting Interview (20-30 min, do annually)
**Say:** "Run goal setting interview" / "Goal setting" / "Set my goals"

What happens:
- Claude asks 10 questions about official goals, shadow goals, success definition, tradeoffs
- You answer
- Claude populates goals/annual_goals_FY26.md, foundation/career_intent_FY26.md, goals/quarterly_focus.md (Q1)
- Claude shows output
- You can edit

**Good for:** Starting year, resetting mid-year if goals changed

**Output:** FY26 goals (declared + shadow) + Q1 focus

---

### Year-in-Review Interview (30-45 min, do at year end)
**Say:** "Run year in review" / "Year in review interview" / "Annual review interview"

What happens:
- Claude asks 15 questions about past year: highlights, surprises, challenges, feedback, learnings, what's next
- You answer
- Claude populates reviews/year_end_review.md, synthesis/year_at_a_glance.md, synthesis/pattern_recognition.md
- Claude offers follow-up questions on any area
- Claude shows output, you can edit

**Good for:** End of year reflection, preparing for official reviews

**Output:** Year-end review, annual narrative, year patterns

---

### Quarterly Reflection Interview (15-20 min, do each quarter)
**Say:** "Run quarterly reflection" / "Q[X] reflection" / "Quarter reflection"

What happens:
- Claude asks 10 questions about quarter: what moved, what mattered, over/under-rotations, surprises, energy, stakeholders, what changes next
- You answer
- Claude populates goals/quarterly_focus.md (next quarter), synthesis/pattern_recognition.md, capture/energy_log.md
- Claude shows output, you can edit

**Good for:** End of quarter reset, quarter planning, pattern identification

**Output:** Next quarter focus, quarter patterns

---

### Manager Relationship Interview (15 min, do when needed)
**Say:** "Run manager relationship interview" / "Manager interview" / "Manager relationship"

What happens:
- Claude asks 10 questions about manager: style, expectations, perception of you, support, tensions, what would help
- You answer
- Claude populates foundation/role_expectations.md, capture/stakeholder_log.md
- Claude shows output, you can edit

**Good for:** Clarifying expectations, tracking manager relationship, mid-year check-ins

**Output:** Your updated role expectations, manager profile

---

## OUTPUT COMMANDS

These generate outputs based on your logs (no input needed).

### Meeting Prep (5 min, instant generation)
**Say:** "Prep me for my 1:1" / "Prep 1:1 with [name]" / "1:1 prep" / "Meeting prep"

What happens:
- Claude reads your recent work_log, wins, goals, feedback
- Claude generates reviews/monthly_1on1_prep.md with focus, impact, blockers, asks, priorities
- Claude shows you the output
- You can edit before taking meeting

**Good for:** Before manager 1:1, before important meetings

**Output:** Meeting prep doc with talking points

---

### Mid-Year Review Generation (10-15 min)
**Say:** "Generate my mid-year review" / "Mid-year review" / "Mid-year self-assessment"

What happens:
- Claude reads Jan-June data from work_log, wins, feedback, goals
- Claude generates reviews/mid_year_review.md
- Claude shows output, you can edit

**Good for:** Preparing for mid-year reviews, mid-year self-assessment, goal progress check

**Output:** Official self-assessment

---

### Year-End Review Generation (15-30 min)
**Say:** "Generate my year-end review" / "Year-end review" / "Annual self-assessment"

What happens:
- Claude offers: "Want to run year-in-review interview first?"
- Claude reads full year of logs
- Claude generates reviews/year_end_review.md (if interview not run) or enhances it (if interview run)
- Claude shows output, you can edit

**Good for:** Preparing for annual reviews, official self-assessment

**Output:** Comprehensive year-end review

---

## INSIGHT COMMANDS

These analyze your data and surface insights.

### Drift Analysis (10 min)
**Say:** "Where am I drifting?" / "Show me drift" / "Am I drifting?"

What happens:
- Claude compares your stated career_intent vs actual work from logs
- Claude compares stated constraints vs decision_log
- Claude compares declared goals vs shadow goals % allocation
- Claude shows analysis: intent vs reality gaps
- Claude offers three options: update intent, course-correct, or acknowledge as conscious tradeoff

**Good for:** Checking alignment, realigning when off-course

**Output:** Drift analysis + recommendations

---

### Pattern Recognition (5 min)
**Say:** "What patterns am I missing?" / "Show me my patterns" / "What patterns exist?"

What happens:
- Claude reads synthesis/pattern_recognition.md (quarterly synthesis)
- Claude shows you: recurring feedback themes, repeated wins, persistent gaps, energy patterns, stakeholder patterns
- Claude flags any blind spots or important insights

**Good for:** Seeing what's unconscious, identifying strengths/gaps, understanding yourself better

**Output:** Your synthesized patterns

---

### Stop-Doing Analysis (10 min)
**Say:** "What should I stop doing?" / "What am I overweight on?" / "What can I cut?"

What happens:
- Claude analyzes work_log using leverage_analysis framework
- Claude identifies low-impact work, energy drains, non-strategic activities
- Claude shows: what to stop, what to delegate, what's killing career momentum

**Good for:** Prioritization, time management, career focus

**Output:** What to stop, delegate, or reduce

---

### Goal Progress Check (5 min)
**Say:** "Am I on track for my goals?" / "Goal progress?" / "How am I doing on goals?"

What happens:
- Claude reads goals/annual_goals_FY26.md and your work_logs
- Claude assesses progress on each goal
- Claude notes what's on track, what's behind, what's ahead
- Claude offers: accelerate, adjust expectations, or refocus

**Good for:** Mid-quarter or mid-year check-ins

**Output:** Goal-by-goal progress assessment

---

## UPLOAD COMMANDS

These process external documents (performance reviews, feedback).

### Extract Patterns from Document (5-10 min, automated)
**Say:** "Extract patterns from this review" / "Synthesize this review" / "Analyze this document"
[Upload PDF or document]

What happens:
- Claude reads document
- Claude extracts: strengths, feedback, gaps, ratings, signals
- Claude updates uploads/document_synthesis.md (extraction log)
- Claude updates uploads/pattern_summary.md (patterns across uploads)
- Claude updates memory.md with insights
- Claude tells you what was found

**Good for:** Processing performance reviews, analyzing 360 feedback, longitudinal feedback analysis

**Output:** Patterns extracted, cross-document synthesis

---

### Synthesize Multiple Reviews (10-15 min, automated)
**Say:** "Synthesize my past reviews"
[Upload multiple reviews]

What happens:
- Claude processes all documents
- Claude creates multi-year pattern analysis
- Claude updates uploads/pattern_summary.md with longitudinal trends
- Claude updates memory.md with career insights

**Good for:** Understanding career trajectory, identifying persistent patterns, long-term blind spots

**Output:** Multi-year pattern analysis

---

## SYSTEM COMMANDS

These help you manage and understand the system.

### View a Document
**Say:** "Show me my [document name]"

Examples:
- "Show me my career intent"
- "Show me my patterns"
- "Show me my quarterly focus"
- "Show me my wins"

What happens:
- Claude displays the document you asked for
- You can read it, edit notes, use it

**Good for:** Reviewing documents anytime, reading your foundation

---

### Status Check
**Say:** "What haven't I updated recently?" / "What's stale?" / "Status check"

What happens:
- Claude checks: when was monthly log last updated? Feedback log? Work log?
- Claude tells you status without guilting you
- Claude offers: "Want to run monthly log now, or skip and resume next month?"

**Good for:** Gentle nudges to update, understanding where you stand

---

### Help Me Restart
**Say:** "Help me restart" / "I fell off" / "Where do I start?" (after gap)

What happens:
- Claude asks: When was your last update?
- Claude guides you: "No backfilling needed. Let's just do [this month]'s work log and resume forward."
- Claude gets you back in with zero guilt

**Good for:** After months away, after being too busy, after life changes

---

## HELP AND TROUBLESHOOTING

### Get Help with System
**Say:** "How do I...?" / "Can I...?" / "What can I do with...?"

Examples:
- "How do I update my goals mid-year?"
- "Can I upload past reviews?"
- "What can I do with my patterns?"

**What happens:** Claude explains how

---

### Something Doesn't Work
**Say:** "This didn't work right" / "[Error message]" / "Help, I got [error]"

**What happens:**
- Claude diagnostics
- Claude fixes it
- Claude summarizes what was wrong and how it's fixed

---

## FREQUENCY GUIDE

**Anytime (No schedule needed):**
- Check-in (whenever you want, 2-5 min)
- Log feedback (immediately when you get it)
- Log decisions (when you make them)
- Log wins (when you ship)

**Monthly:**
- Work log (end of month, 20-30 min) ← This is the cornerstone
- 1:1 prep (before manager meeting, 5 min)

**Quarterly:**
- Quarterly reflection interview (end of quarter, 15-20 min)
- Pattern review (auto-generated, just read)

**Annually:**
- Goal-setting interview (start of FY, 20-30 min)
- Year-in-review interview (end of FY, 30-45 min)
- Year-end review generation (auto-generated, for official reviews)
- Upload past reviews (when you receive them)

**As Needed:**
- Drift analysis (when you feel off-track)
- Stop-doing analysis (when overwhelmed)
- Pattern review (anytime you want to understand yourself)
- Manager interview (when expectations unclear)

---

## MINIMUM VIABLE USAGE

If you can only do one thing: **Monthly log** (20-30 min)

Everything else is bonus. The system still works and helps you.

If you can only do two things: **Monthly log + Check-in** (anytime)

---

## TIPS FOR BEST USE

- **Be conversational.** Don't worry about exact wording. "Quick check-in", "Do a check-in", "Check in today" all work.
- **Let Claude format.** You give raw answers. Claude makes them pretty.
- **Review before saving.** Claude shows you everything before saving. Feedback is welcome.
- **Capture monthly minimum.** Miss a week? That's fine. Do monthly.
- **Use check-ins for momentum.** Anytime quick reflection keeps you thinking about work.
- **Upload reviews when you get them.** Don't wait—patterns emerge.
- **Run quarterly reflection at quarter end.** Resets your thinking for next quarter.
- **Read your patterns quarterly.** Understanding yourself is powerful.

---

## Quick Reference Table

| What | Command | Time | Frequency |
|------|---------|------|-----------|
| Quick reflection | "Check-in" | 2-5 min | Anytime |
| Monthly capture | "Monthly log" | 20-30 min | Monthly |
| Log accomplishment | "Log this win" | 3-5 min | As it happens |
| Log feedback | "Log this feedback" | 2-3 min | Immediately |
| Log decision | "Log this decision" | 2-3 min | When decided |
| Set foundation | "Career identity interview" | 20-30 min | Once, or when direction shifts |
| Set goals | "Goal setting interview" | 20-30 min | Annual |
| Annual reflection | "Year in review interview" | 30-45 min | Annual |
| Quarter check | "Quarterly reflection interview" | 15-20 min | Quarterly |
| Manager alignment | "Manager relationship interview" | 15 min | As needed |
| Meeting prep | "Prep me for my 1:1" | 5 min | Monthly |
| Mid-year review | "Generate my mid-year review" | 10-15 min | Mid-year |
| Year-end review | "Generate my year-end review" | 15-30 min | Year-end |
| See patterns | "What patterns am I missing?" | 5 min | Quarterly |
| Check alignment | "Where am I drifting?" | 10 min | As needed |
| Stop-doing list | "What should I stop doing?" | 10 min | As needed |
| Process review | "Extract patterns from this review" | 5 min | When received |
| Check status | "What haven't I updated recently?" | 2 min | Whenever |
| Get back on track | "Help me restart" | 10 min | After gap |

---

## Remember

You're talking to Claude Code, not managing a system. That's the whole point.

Say these things. Claude handles the rest.

See QUICK_START.md to get started right now.
