# Log formats

One file per kind per calendar year, named by the date of the event: `wins_2026.md`, `wins_2027.md`. Claude creates a file with its first entry. New entries go at the end. Leave out a line the user said nothing about, except where it says "not given".

## `work_YYYY.md` (monthly)

```
## YYYY-MM
**Shipped:**
**Impact:**
**Invisible work:**
**Didn't work:**
**Surprises:**
**Still open:**
```

Mark a month "partial" until `/monthly-log` has been run for it.

## `wins_YYYY.md`

```
## YYYY-MM-DD: Short title
**What:**
**Why it mattered:**
**Who benefited:**
**Evidence:** numbers, quotes or links, or "not given"
**Goal:** goal name, or "unplanned"
```

## `feedback_YYYY.md`

```
## YYYY-MM-DD: Short title
**Feedback:** "exact words"
**From:** name, role, setting
**My read:**
**Action:** what they will do, or "none yet"
```

## `decisions_YYYY.md`

```
## YYYY-MM-DD: Short title
**Decision:**
**Why:**
**Tradeoff:**
**Fits foundation?** yes, or quote what it pulls against
```

## `check_ins_YYYY.md`

```
## YYYY-MM-DD
**Energy:** 1-10
**Wins:**
**Friction:**
**Next:**
```

## `people.md` (one file, not yearly)

```
## Name, role
**What they care about:**
**How we work together:**
**Dated notes:**
```
