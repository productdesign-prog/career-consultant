---
name: resume-rewriter
description: Rewrite resume bullets and sections to match a target role or vacancy WITHOUT inventing experience. Use when the user asks to rewrite, improve, tailor, or adapt their resume bullets/sections for a role — "rewrite my experience for this job", "make my bullets stronger", "адаптируй резюме под вакансию". Produces concrete before/after rewrites using a fixed formula, marks anything missing as [NEED DATA] and anything uncertain as [VERIFY]. Keeps a master resume and creates only vacancy-specific variants — never overfits the master to one posting.
---

# Resume Rewriter

Turn weak, vague, or generic resume lines into concrete, truthful ones aligned to a target role — without ever fabricating experience. The deliverable is a set of before/after edits the user can paste in.

## Rules (non-negotiable — they protect the user in interviews)

1. Don't invent facts or metrics. 2. Don't invent or inflate seniority. 3. Don't claim sole ownership when the user only contributed. 4. Mark uncertain facts `[VERIFY]`, missing evidence `[NEED DATA]`. 5. Preserve truthful scope. 6. Prefer concrete outcomes over adjectives. 7. Remove vague claims. 8. Use target-role vocabulary only when the experience actually supports it.

## Bullet formula

Did X for Y audience/context, using Z method/tool, resulting in a measurable or observable outcome.

**Example**
- Bad: "Passionate UX designer with strong research skills."
- Better: "Led evaluative research for [product/context], identifying [N] usability issues `[NEED DATA]` and translating findings into [design/product outcome]."

## Three-layer model (anti-overfitting — read this first)

Career agents that rewrite the whole resume for every posting quietly destroy the candidate's coherent story after 20–30 vacancies. Prevent that with three explicit layers:

```
Master Resume        ← the truthful, complete record. NEVER auto-edit it.
   ↓ (tailor)
Target Role Resume   ← one per target role; emphasis/ordering for that role family
   ↓ (tailor)
Vacancy Variant      ← per posting; small, surgical tweaks for one vacancy
```

Rules:
- Treat the **Master Resume** as read-only. You may *suggest* additions to it (e.g. a `[NEED DATA]` the user later fills), but never silently rewrite it — changes to the Master require the user's explicit say-so.
- A **Target Role Resume** is derived from the Master: reorder, foreground, trim — never add experience the Master doesn't contain.
- A **Vacancy Variant** is the smallest possible diff from the Target Role Resume — only what this one posting needs. Save it as a separate file/version so the Master and Target stay clean.
- Always name which layer you're editing in your output.

## How to work

1. Anchor to a target: a specific vacancy if available, else the market requirements profile, else the target role. Decide which layer you're producing (Target Role Resume vs Vacancy Variant).
2. Go bullet by bullet. For each: show the original, the rewrite, and a one-line reason tied to the target. Where a number would make the bullet land but isn't in the source, insert a `[NEED DATA]` slot rather than a guessed figure.
3. Flag claims that read stronger than the evidence with `[VERIFY]` and suggest a truthful softer phrasing.
4. Never write changes back into the Master. Produce variants as separate outputs.

## Output — Resume Patch Suggestions

A list of edits (section → original → rewrite → reason), plus a short list of `[NEED DATA]` items the user should fill in, and any `[VERIFY]` flags. End with which edits matter most for the target.

Hand off to `resume-ats-reviewer` if the user also wants the structural/ATS pass.
