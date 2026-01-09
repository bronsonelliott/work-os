# Wins Ledger

*Evidence-based accomplishments (Julia Evans' Brag Document)*
*Time estimate: 5-10 minutes per entry, or add from monthly_log extraction*
*Added through: "Log this win" command or auto-extracted from monthly_log*

---

## Entry Structure

```
## [Accomplishment Title]

**What:** [Specific thing you did]

**Why It Mattered:** [Impact, value, benefit created]

**Who Benefited:** [Stakeholders affected]

**Evidence:** [Metrics, quotes, links, before/afters]

**Skills Demonstrated:** [What this shows about your capabilities]
```

---

## Sample Entries

### Excellent Win Entry

```
## Built Subscription Intelligence Pipeline

**What:** Python automation pulling 714k daily subscription records, processing with Claude API to generate executive briefing posted to Slack each morning

**Why It Mattered:** 
- Saved executives 2 hours/week reading reports manually
- Caught 3 critical anomalies including $50k revenue leak
- Became template for AI analytics across company

**Who Benefited:**
- VP Business Ops (primary user)
- Finance team (data quality improvements)
- 3 other teams now using template
- Entire company (prevented revenue loss)

**Evidence:**
- 60 Slack reactions in 90 days
- 500 hours/year time savings calculation
- VP quote: "This is now my first stop every morning"
- GitHub repo with 3 teams that adopted code
- 3 documented uses of template

**Skills Demonstrated:**
- Python + Claude API integration
- n8n orchestration
- Executive communication (simple compelling briefing)
- Proactive problem-solving (identified need before asked)
- AI implementation expertise
```

### Good Win Entry

```
## Mentored Sarah to Promotion

**What:** 8-month weekly 30-minute mentoring sessions on analytics, SQL, Python, and executive communication

**Why It Mattered:** 
- Sarah promoted to Senior Analyst in 12 months (faster than org average 18 months)
- She now mentors 2 other analysts (multiplier effect)
- Demonstrates ability to develop people, not just write code

**Who Benefited:**
- Sarah (career advancement)
- 2 analysts Sarah now mentors
- Team (developed internal expertise)

**Evidence:**
- Promotion packet cites mentoring relationship
- Manager quote: "[Name] developed Sarah into someone ready 6 months early"
- Sarah quote: "Mentoring from [Name] made all the difference"
- 2 analysts Sarah is now mentoring

**Skills Demonstrated:**
- Mentoring and leadership
- Clear communication
- Investment in people
- Patience and teaching ability
```

---

## Integration Points

Sources: work_log.md (auto-extracted), add_win command, check_in_log.md (good wins)
Used for: Review prep, 1:1 talking points, promotion evidence, career narrative
Analyzed for: Repeated win types = natural strengths

Claude will:
- Extract potential wins from monthly_log and ask if you want to add
- Help format wins with good evidence
- Flag if win lacks evidence ("while it's fresh?")
- Identify patterns (3+ same type = strength)

---

## Quality Tips

- **Be specific:** "Built dashboard" → "Built subscription dashboard reducing reporting time from 4 hours to 15 minutes"
- **Include evidence:** Metrics, quotes, links, screenshots, adoption numbers
- **Note impact:** Who benefited? How much value?
- **Add skills:** What does this win demonstrate about you?
- **Update as evidence compounds:** "Now used by 5 teams" replaces "Used by 1 team"
