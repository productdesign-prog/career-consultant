---
name: job-match-scorer
description: Score a specific vacancy against the user's profile and resume, 0–100, and decide apply / maybe / reject / do-not-apply. Use whenever the user shares a job link or job text and asks "should I apply", "is this a good fit", "score this role", "оцени вакансию". Applies hard-stop rules, ALWAYS shows the weighted score breakdown, a separate confidence score, and an explicit requirement→evidence map tied to the user's profile. Only recommends applying at ≥ 80. Never inflate the user's experience to clear the threshold.
---

# Job Match Scorer

Decide, with reasons, whether a vacancy is worth the user's effort. A high score is a claim you must back with evidence from the user's profile. The number must be *computed*, never vibed — if you can't show how the parts sum to the total, you haven't scored it.

## Steps

1. Parse the vacancy: required vs preferred, responsibilities, level, location/format, language, comp if stated.
2. Run hard-stop checks first. Any hit → reject / do-not-apply regardless of total.
3. Score each rubric category using the fixed weights in `references/scoring-rubric.yaml`. Tie every sub-score to concrete evidence in the user's resume/profile.
4. Sum to a 0–100 total. The total MUST equal the sum of the sub-scores.
5. Compute a separate **confidence** score (how reliable the match number is — different from the match itself).
6. Build the requirement → evidence map.
7. Decide and explain.

## Mandatory output — Job Match Report

Always include every section below, in this shape. The breakdown and the confidence line are not optional — without them an "82" vs "86" is meaningless intuition.

```
Company: …    Role: …    Link: …    Date analyzed: …

DECISION: Apply | Maybe | Reject | Do not apply

Match score: TOTAL/100
  Role fit:           x/20
  Must-have skills:   x/25
  Domain fit:         x/10
  Evidence strength:  x/15
  Location fit:       x/10
  Compensation fit:   x/5
  Keyword coverage:   x/10
  Strategic value:    x/5
  (sub-scores must sum to TOTAL)

Confidence: NN%  — reason: [what limits reliability]

Hard-stop checks: [each check → pass/fail]

Requirement → Evidence map:
  Requirement: [exact vacancy requirement]
    Evidence:  Resume → [Company/section] → [specific line]   (or: NONE)
    Strength:  Strong | Medium | Weak | Missing
  … one row per must-have and major preferred requirement

Missing requirements: [unmet, with whether honestly compensable]
Risks: [separate from gaps — what could go wrong even if you qualify]
How to position the application: …
Resume changes needed: … (hand to resume-rewriter)
Cover letter angle: … (only if Apply)
Final recommendation: …
```

## Confidence model

Confidence answers "how much should the user trust this number?" — it is independent of the score. Start near 100% and subtract for each reliability gap, then state the reasons:

- Vacancy text incomplete / vague → large reduction.
- No portfolio or work samples where the role expects them → reduction.
- Missing data on a scored dimension (e.g. no domain info in the profile) → reduction.
- Requirements you had to infer rather than read → reduction.
- Single ambiguous source for the posting → reduction.

A score of 85 at 42% confidence is a signal to gather more data before acting — say so explicitly.

## Evidence mapping (why this matters)

Without an explicit requirement → evidence map, "match" silently degrades into keyword matching. For each requirement, name the *actual line* in the resume that supports it and rate the strength. "Missing" is a valid, useful answer — it shows the user exactly what to shore up. Never invent evidence; if there's none, mark it Missing and let it pull the score down.

## Hard-stops (reject regardless of score)

A required language the user lacks at the needed level · a required location the user can't be in (and won't relocate to) · a required experience the user lacks and can't honestly compensate for · company/industry on the user's exclusion list (→ Do not apply) · salary below the user's floor · role too far from the user's target trajectory · scam / fake / lead-gen posting · posting too vague to analyze.

## After scoring

Offer to update the tracker (`career-tracker`). Proceed to an application package only at ≥ 80 with no hard-stop, and only after the user confirms. For "which roles to even chase" questions that sit above a single vacancy, hand off to `career-strategist`.

## Acceptance bar

Good: weighted breakdown that sums to the total, separate confidence with reasons, requirement→evidence map, hard-stops checked, gaps separated from risks, decision consistent with the threshold. Fail: a bare "good fit", a total with no breakdown, ≥ 80 without evidence, ignoring an unmet hard requirement, confidence omitted.
