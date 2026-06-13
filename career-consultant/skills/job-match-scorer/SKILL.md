---
name: job-match-scorer
description: Score a specific vacancy against the user's resume on SKILLS ONLY (0–100) and decide apply / maybe / reject. Use whenever the user shares a job link or job text and asks "should I apply", "is this a good fit", "score this role", "оцени вакансию". The score reflects ONLY whether the candidate's resume skills cover the skills the vacancy asks for. Seniority/grade, domain/industry, location, pay, format, and language are reported as non-blocking flags — they never change the score or decision, to keep the funnel wide. ALWAYS shows the weighted breakdown, a separate confidence score, and a skill→evidence map. Never inflate the user's experience to clear the threshold.
---

# Job Match Scorer

The score answers exactly one question: **do the candidate's skills (as shown in their resume) cover the skills this vacancy asks for?** Nothing else enters the number.

## Score skills only — everything else is a flag (read this first)

Score ONLY skills/competencies. Do **not** let any of these touch the score or the decision — report each as a flag instead:

- **Seniority / grade** — if the role is Middle and the candidate is Lead (or vice versa), that is a FLAG, not a deduction. Do not lower the score for grade mismatch.
- **Domain / industry** — consumer vs B2B, fintech vs medtech, etc. is a FLAG. Do not lower the score because the candidate's domain differs.
- **Location, work format, timezone, relocation** — flags.
- **Compensation / salary** (including "unknown") — a flag. Never let unknown or low pay reduce the score.
- **Language as logistics, industry exclusions** — flags.

If you ever find yourself writing "doesn't reach the threshold because of [grade / domain / pay / location]", stop — that belongs in flags, not in the score.

## Steps

1. From the vacancy, extract the list of required + preferred **skills/competencies**. Separately note the conditions for the flags section (grade, domain, location, pay, format, language).
2. Score the three capability categories in `references/scoring-rubric.yaml`, tying each to lines in the resume.
3. Sum to a 0–100 total (must equal the sum of sub-scores). An unmet skill costs coverage points; it never auto-rejects.
4. Compute a separate **confidence** score.
5. Build the skill → evidence map.
6. List the non-scoring flags.
7. Decide from the skills score alone.

## Mandatory output — Job Match Report

```
Company: …    Role: …    Link: …    Date analyzed: …

DECISION: Apply | Maybe | Reject        (from the skills score ONLY)

Skills match: TOTAL/100
  Required-skills coverage:  x/55
  Evidence strength:         x/30
  Keyword coverage:          x/15
  (sub-scores must sum to TOTAL)

Confidence: NN%  — reason: [what limits reliability]

Skill → Evidence map:
  Skill required: [exact skill/competency from the vacancy]
    Evidence:  Resume → [Company/section] → [specific line]   (or: NONE)
    Strength:  Strong | Medium | Weak | Missing
  … one row per required and major preferred skill

Flags (do NOT affect score or decision — for the user to weigh):
  Seniority/grade: [role level vs candidate]   ← never scored
  Domain/industry: [vacancy vs candidate]      ← never scored
  Location/format: [vacancy vs candidate]
  Compensation:    [stated / unknown vs floor]
  Language:        [required vs candidate]
  Integrity:       [⚠ only if the posting looks fake/scam/lead-gen]

Missing skills: [unmet skills, with whether honestly compensable]
Risks: [what could go wrong even if the skills fit]
How to position the application: …
Resume changes needed: … (hand to resume-rewriter)
Cover letter angle: … (only if Apply)
Final recommendation: …
```

## Decisions (funnel-wide, skills score only)

- **Apply**: skills score ≥ 70.
- **Maybe**: 45–69.
- **Reject**: < 45.

Flags never move the decision. If a flag looks like a dealbreaker for this user (e.g. pay below floor), say so in the flags and let them choose — don't reject for them. A grade or domain mismatch with strong skill coverage is still an Apply.

## Confidence model

Confidence answers "how much should the user trust this number?" — independent of the score. Start near 100% and subtract for each reliability gap, stating reasons: vacancy text vague; no portfolio where the role expects samples; missing data on a skill; skills you had to infer rather than read; single ambiguous source. A score of 85 at 42% confidence means "gather more data before acting" — say so.

## Evidence mapping (why this matters)

Without an explicit skill → evidence map, "match" silently degrades into keyword matching. For each required skill, name the *actual line* in the resume that supports it and rate strength. "Missing" is valid and useful — it shows exactly what to shore up. Never invent evidence; if there's none, mark Missing and let it pull coverage down.

## After scoring

Offer to update the tracker (`career-tracker`). An application package needs a skills score in the Apply band and the user's confirmation. For "which roles to even chase" questions — where grade, domain, pay and trajectory legitimately belong — hand off to `career-strategist`.

## Acceptance bar

Good: skills-only breakdown summing to the total, confidence with reasons, skill→evidence map, grade/domain/location/pay listed strictly as non-scoring flags, decision from the skills score. Fail: grade/domain/pay/location moving the score or the decision, a total with no breakdown, ≥ threshold without evidence, confidence omitted.
