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

## How to work

1. Anchor to a target: a specific vacancy if available, else the market requirements profile, else the target role.
2. Go bullet by bullet. For each: show the original, the rewrite, and a one-line reason tied to the target. Where a number would make the bullet land but isn't in the source, insert a `[NEED DATA]` slot rather than a guessed figure.
3. Flag claims that read stronger than the evidence with `[VERIFY]` and suggest a truthful softer phrasing.
4. Keep the **master resume** intact. Produce vacancy-specific variants as separate outputs so the user doesn't overfit the master to one posting.

## Output — Resume Patch Suggestions

A list of edits (section → original → rewrite → reason), plus a short list of `[NEED DATA]` items the user should fill in, and any `[VERIFY]` flags. End with which edits matter most for the target.

Hand off to `resume-ats-reviewer` if the user also wants the structural/ATS pass.
