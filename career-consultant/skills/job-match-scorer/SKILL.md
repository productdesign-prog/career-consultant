---
name: job-match-scorer
description: Score a specific vacancy against the user's profile and resume on SKILLS/CAPABILITY only (0–100), and decide apply / maybe / reject. Use whenever the user shares a job link or job text and asks "should I apply", "is this a good fit", "score this role", "оцени вакансию". The score measures whether the candidate can do the job — conditions (location, pay, format, language, industry) are reported as flags only and never change the score or decision, to keep the funnel wide. ALWAYS shows the weighted breakdown, a separate confidence score, and a requirement→evidence map. Never inflate the user's experience to clear the threshold.
---

# Job Match Scorer

Decide whether a vacancy is worth pursuing, based on whether the candidate **can do the job**. The score is a capability claim you must back with evidence from the user's profile. The number is *computed*, never vibed — if you can't show how the parts sum to the total, you haven't scored it.

## Score skills, not conditions (core design)

The match score measures capability only: skills, role fit, evidence, domain, keyword overlap. Conditions — location, compensation, work format, language-as-logistics, industry — are **flags**, reported for the user's awareness. They never reduce the score and never force a reject. The point is to keep the funnel as wide as possible and let the user decide which conditions are dealbreakers for them. There are no condition-based hard-stops.

## Steps

1. Parse the vacancy: required vs preferred *skills/competencies*, responsibilities, level, scope. Separately note the conditions (location, comp, format, language, industry) for the flags section.
2. Score each capability category using the fixed weights in `references/scoring-rubric.yaml`. Tie every sub-score to concrete evidence in the user's resume/profile.
3. Sum to a 0–100 total. The total MUST equal the sum of the sub-scores. An unmet must-have skill simply costs its points — it does not auto-reject.
4. Compute a separate **confidence** score (how reliable the match number is — different from the match itself).
5. Build the requirement → evidence map.
6. List condition flags (informational, non-blocking).
7. Decide from the skills score alone, and explain.

## Mandatory output — Job Match Report

```
Company: …    Role: …    Link: …    Date analyzed: …

DECISION: Apply | Maybe | Reject        (from the skills score only)

Skills match: TOTAL/100
  Must-have skills:   x/35
  Role fit:           x/25
  Evidence strength:  x/25
  Domain fit:         x/10
  Keyword coverage:   x/5
  (sub-scores must sum to TOTAL)

Confidence: NN%  — reason: [what limits reliability]

Requirement → Evidence map:
  Requirement: [exact skill/competency from the vacancy]
    Evidence:  Resume → [Company/section] → [specific line]   (or: NONE)
    Strength:  Strong | Medium | Weak | Missing
  … one row per must-have and major preferred skill

Condition flags (do NOT affect score or decision — for your awareness):
  Location:    [vacancy vs user]  → note
  Compensation:[vacancy vs user]  → note
  Format:      [remote/hybrid/onsite vs user]
  Language:    [required vs user]
  Industry:    [note if on the user's watch/exclusion list]
  Integrity:   [⚠ only if the posting looks fake/scam/lead-gen]

Missing skills: [unmet, with whether honestly compensable]
Risks: [separate from gaps — what could go wrong even if you qualify]
How to position the application: …
Resume changes needed: … (hand to resume-rewriter)
Cover letter angle: … (only if Apply)
Final recommendation: …
```

## Decisions (funnel-wide)

- **Apply**: skills score ≥ 75.
- **Maybe**: 55–74.
- **Reject**: < 55.

Conditions never move the decision. If a condition looks like a dealbreaker for this user, say so in the flags and let them choose — don't reject for them.

## Confidence model

Confidence answers "how much should the user trust this number?" — independent of the score. Start near 100% and subtract for each reliability gap, then state the reasons:

- Vacancy text incomplete / vague → large reduction.
- No portfolio or work samples where the role expects them → reduction.
- Missing data on a scored dimension (e.g. no domain info in the profile) → reduction.
- Requirements you had to infer rather than read → reduction.
- Single ambiguous source for the posting → reduction.

A score of 85 at 42% confidence is a signal to gather more data before acting — say so explicitly.

## Evidence mapping (why this matters)

Without an explicit requirement → evidence map, "match" silently degrades into keyword matching. For each skill requirement, name the *actual line* in the resume that supports it and rate the strength. "Missing" is a valid, useful answer — it shows the user exactly what to shore up. Never invent evidence; if there's none, mark it Missing and let it pull the score down.

## After scoring

Offer to update the tracker (`career-tracker`). An application package needs a skills score in the Apply band and the user's confirmation. For "which roles to even chase" questions above a single vacancy, hand off to `career-strategist`.

## Acceptance bar

Good: weighted skills breakdown that sums to the total, separate confidence with reasons, requirement→evidence map, conditions listed as non-blocking flags, decision from the skills score. Fail: a bare "good fit", a total with no breakdown, conditions dragging down the score or forcing a reject, ≥ threshold without evidence, confidence omitted.
