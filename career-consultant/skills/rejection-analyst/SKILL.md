---
name: rejection-analyst
description: Turn rejections and recruiter feedback into structured learning that updates the user's profile and future strategy. Use when the user reports a rejection, ghosting, or interview feedback — "didn't get it", "got rejected", "recruiter said…", "не прошёл собес", "отказали после интервью". Extracts the likely reason, distinguishes signal from noise across multiple rejections, and proposes concrete profile/positioning/targeting updates. Most career tools only analyze vacancies; this one learns from outcomes.
---

# Rejection Analyst

The most valuable feedback in a job search isn't the market — it's the user's own rejections. Close the loop:

```
Application → Interview → Rejection/Feedback → Reason extraction → Profile & strategy update
```

## What to do with a single rejection

1. Capture the facts: stage reached (no response / screen / interview / test task / final), role, company, what was said (if anything), and timing.
2. Extract the **likely reason**, and be honest about certainty — most rejections come with no real explanation. Separate:
   - **Stated reason** (what they told the user — often diplomatic, sometimes real).
   - **Inferred reason** (your read, marked as inference, with confidence).
   - **Unknown** (say so rather than inventing a cause).
3. Classify the reason: fit/seniority, missing hard skill, evidence too weak, comp mismatch, location/logistics, communication/language, portfolio gap, timing/headcount, or no-signal (ghosting).
4. Propose at most 2–3 concrete actions tied to that reason — and only if the reason is reasonably supported.

Resist over-fitting to one data point. A single rejection rarely justifies rewriting the strategy; say when the right move is "log it and wait for the pattern".

## What to do across many rejections (pattern analysis)

When the tracker has several rejections, look for recurring signal:

```
Rejections analyzed: 9
Reached interview: 6/9   → top-of-funnel is fine; conversion is the problem
Recurring theme: "looking for more <X> domain depth" (4/9)
Recurring theme: comp above range (2/9)
```

Report: where in the funnel the user loses most often, the recurring themes (with counts), and whether the issue is **targeting** (wrong roles), **packaging** (resume/cover letter/positioning), or **performance** (interview/test task). Each diagnosis routes differently — targeting → `career-strategist`; packaging → `resume-rewriter` / `resume-ats-reviewer` / `cover-letter-writer`; performance → interview prep guidance.

## Updating the profile

Translate confirmed patterns into edits to the user's working files — e.g. add a `[NEED DATA]` for missing proof, adjust the hard-stop list (comp floor, domains), or revise positioning. Never invent experience to "fix" a rejection. Always get the user's confirmation before changing `constraints.md` or the master profile.

## Output

A short Rejection Report: facts → reason (stated/inferred/unknown + confidence) → classification → funnel position → recommended actions (≤3) → which skill to route to → whether to update any working file. Then offer to log it in `career-tracker` (rejection reason, feedback, learning).
