---
name: job-match-scorer
description: Score a specific vacancy against the user's profile and resume, 0–100, and decide apply / maybe / reject / do-not-apply. Use whenever the user shares a job link or job text and asks "should I apply", "is this a good fit", "score this role", "оцени вакансию". Applies hard-stop rules, shows the score breakdown, ties evidence to the user's profile, and only recommends applying at ≥ 80. Never inflate the user's experience to clear the threshold.
---

# Job Match Scorer

Decide, with reasons, whether a vacancy is worth the user's effort. A high score is a claim you must back with evidence from the user's profile.

## Steps

1. Parse the vacancy: required vs preferred, responsibilities, level, location/format, language, comp if stated.
2. Run hard-stop checks first (see below). Any hit → the vacancy is rejected or "do not apply" regardless of score.
3. Score each category, tying points to concrete evidence in the user's resume/profile.
4. Sum to a 0–100 score, state a separate confidence level.
5. Decide and explain.

## Scoring rubric (0–100)

| Category | Points |
|---|---|
| Role fit (title, seniority, task type, scope, IC/lead) | 20 |
| Must-have skills (an unmet hard requirement → reject even if total is high) | 25 |
| Domain / industry fit | 10 |
| Evidence strength (metrics, shipped outcomes, scale, decisions, research, portfolio) | 15 |
| Location / logistics (geo, timezone, visa/relocation, format, language) | 10 |
| Compensation / constraints fit | 5 |
| Resume keyword coverage (without stuffing) | 10 |
| Strategic value | 5 |

## Hard-stops (reject regardless of score)

- A required language the user doesn't have at the needed level.
- A required location the user can't be in (and won't relocate to).
- A required experience the user lacks and can't honestly compensate for.
- The company/industry is on the user's exclusion list → "Do not apply".
- Salary below the user's floor, if set.
- Role too far from the user's target trajectory.
- Looks like a scam, fake posting, or lead-gen.
- Posting too vague to analyze reliably.

## Decisions

- **Apply**: ≥ 80 and no hard-stop.
- **Maybe**: 70–79, or compensable gaps.
- **Reject**: < 70, or an unmet hard requirement.
- **Do not apply**: conflicts with the user's constraints.

## Report structure — Job Match Report

Company · Role · Link · Date analyzed · Match score · Decision · Hard-stop checks · Score breakdown · Must-have match · Missing requirements · Evidence from user profile · Risks · How to position the application · Resume changes needed · Cover letter angle · Confidence level · Final recommendation.

After scoring, offer to update the tracker (`career-tracker`). Only proceed to an application package at ≥ 80 with no hard-stop, and only after the user confirms.

## Acceptance bar

Good: full breakdown, hard-stops checked, evidence tied to the profile, gaps explicit, decision consistent with the threshold. Fail: a bare "good fit / bad fit", ignoring missing hard requirements, ≥ 80 without evidence, recommending weak matches.
