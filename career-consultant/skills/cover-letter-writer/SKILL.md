---
name: cover-letter-writer
description: Write a short, specific cover letter for a vacancy using only verified facts from the user's resume/profile. Use when the user wants a cover letter, application letter, or "письмо рекрутёру/сопроводительное" for a specific role. Maximum 3 paragraphs and ~220 words, no generic enthusiasm or clichés, two or three evidence-based overlaps with the role, and one concrete reason for interest in the company. Only write once the vacancy is in the Apply band (skills score ≥ 75 via job-match-scorer) and the user confirms.
---

# Cover Letter Writer

Write a letter that sounds like a competent human wrote it in ten focused minutes — not an LLM filling a template. Short, specific, evidence-based, no filler.

## Preconditions

Only draft a letter for a vacancy in the **Apply band (skills score ≥ 75)** from `job-match-scorer`, and after the user confirms. If it hasn't been scored, score it first or say why you're not writing yet. Use only facts present in the user's resume/profile — no invented motivation or claims.

## Rules

- Max 3 paragraphs, max ~180–220 words.
- No generic enthusiasm, no autobiography, no restating the resume, no empty adjectives, no unsupported claims.
- Tie 2–3 concrete parts of the user's experience to the role's stated needs.
- One specific, real reason for interest in the company.
- Dry, professional close — no flourish.

## Stop-slop list (banned or unwanted phrases)

I am excited to apply · I am thrilled · I am passionate about · perfect fit · dynamic team · fast-paced environment · leverage my skills · proven track record · uniquely qualified · I believe my background makes me · innovative solutions · cutting-edge · make an impact · strong communication skills · team player · results-driven · detail-oriented · highly motivated · I would welcome the opportunity · Thank you for your time and consideration.

If a draft contains any of these, rewrite before delivering.

## Plain alternatives

"Your role appears to require…" · "My relevant experience is…" · "The strongest overlap is…" · "I would focus on…" · "This is worth discussing because…".

## Self-check before delivering

≤ 3 paragraphs? ≤ 220 words? Zero stop-slop phrases? No invented facts? Specific to this company and role? A clear, real reason to talk? If any answer is no, fix it. Then offer to log the version in `career-tracker`.
