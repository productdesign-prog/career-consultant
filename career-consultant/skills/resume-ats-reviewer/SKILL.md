---
name: resume-ats-reviewer
description: Review a resume/CV against a target role and (optionally) a specific vacancy, in two lenses — market-fit and ATS parseability. Use whenever the user wants to check, audit, improve, or "ATS-proof" a resume; mentions ATS, applicant tracking systems, keyword coverage, resume review, CV review, "проверь резюме", "ATS-проверка", "почему меня не зовут на интервью"; or pastes a resume and a job description and asks how well they match. Produces a prioritized, bullet-level edit list — never generic "improve your wording" advice. Do NOT fabricate facts or metrics; mark missing data as [NEED DATA] and uncertain claims as [VERIFY].
---

# Resume ATS Reviewer

Review a resume against (1) the requirements of a target role/market and (2) ATS parseability. The output is a concrete, prioritized list of edits the person can act on today — not vague encouragement.

Two hard commitments shape everything:

- **Truth over optimization.** Never invent experience, metrics, titles, scope, or dates. ATS keyword coverage must never be bought by making the resume less true or less readable to a human. If a strong bullet needs a number the resume doesn't contain, mark it `[NEED DATA]` rather than guessing. If a claim looks inflated or unverifiable, mark it `[VERIFY]`.
- **Specificity over platitudes.** "Strengthen your summary" is useless. "Replace line 3 of the summary with X because the vacancy asks for Y" is the job. Every recommendation points at a concrete location and gives the rewrite or the exact gap.

## Inputs

Required: the resume (file or pasted text) and the target role/title. Ask if missing.

Helpful: a specific vacancy (turns market-fit into precise matching), target seniority, and a market requirements profile if one exists (e.g. from `market-analyst`). With only a resume and a role, proceed but say the ATS keyword section is directional and lower your stated confidence.

## Reading the resume

For PDF/DOCX/DOC, extract the text first: DOC/RTF via libreoffice (`libreoffice --headless --convert-to txt`), DOCX via the docx skill or pandoc, PDF via the pdf skill. Read the *actual* text and note how the file is structured — tables, columns, headers/footers, and text-in-images are exactly what ATS review is about.

## Output: Resume Review Report (two blocks, in this order)

### Block 1 — Market-fit review
1. Target role (+ seniority).
2. Market requirements used (and their source — vacancy, market scan, or role knowledge; confidence depends on it).
2b. **Requirement → evidence map** — the heart of a real review (without it, ATS work collapses into keyword matching). For each key requirement, name the actual supporting line and rate it:
```
Requirement: [exact requirement]
  Evidence:  Resume → [Company/section] → [specific line]   (or: NONE)
  Strength:  Strong | Medium | Weak | Missing
```
"Missing" is a valid, valuable answer — it shows exactly what to shore up. Never invent evidence.
3. Current positioning (1–2 lines).
4. Strong sections (keep/foreground).
5. Weak sections (with reasons).
6. Missing proof — claims without evidence; tag `[NEED DATA]`.
7. Skills underrepresented (has them, buried/omitted).
8. Skills overclaimed (reads stronger than evidence); tag `[VERIFY]`.
9. Recommended section changes (reorder/add/cut, with why).
10. Bullet-level fixes — the core. For each: quote the current bullet, give the rewrite, name the reason. Use the bullet formula. Tag inserted facts `[NEED DATA]`.
11. Priority changes — P1/P2/P3, P1 = most affects passing screening.

### Block 2 — ATS review
Parseability and keyword alignment, not folklore — there are no magic "ATS hacks", just clean structure and the right words present in context.
1. File format (parseable? scanned PDF/image = risky).
2. Layout risk (multi-column, tables, text boxes, header/footer content) — name the offending elements.
3. Heading clarity (standard, machine-readable headings).
4. Keyword coverage — present vs. missing lists.
5. Role-title alignment with the vacancy's title language.
6. Experience chronology (reverse-chronological, consistent dates).
7. Bullet readability (parseable lines, not run-on or table-buried).
8. Keyword stuffing risk (flag gaming — it hurts humans and some parsers).
9. Missing exact terms from the vacancy (mirror precise strings where truthful).
10. ATS-safe rewrite suggestions (flatten this table; move skills out of the sidebar; rename headings).

### Close with
- Confidence: NN% + reason (lower it when there's no specific vacancy to match against, the resume is partial, or the role expects samples/portfolio you can't see).
- Top 3 actions (highest-payoff edits, restated to start immediately).

## Bullet rewriting rules
1. No invented facts/metrics. 2. No inflated seniority. 3. No claiming sole ownership of team work. 4. Tag uncertain `[VERIFY]`, missing `[NEED DATA]`. 5. Preserve truthful scope. 6. Concrete outcomes over adjectives. 7. Remove vague claims. 8. Target-role vocabulary only when supported.

**Bullet formula:** Did X for Y audience/context, using Z method/tool, resulting in a measurable or observable outcome.

**Example** — Weak: "Passionate designer with strong research skills." Better: "Led evaluative research for [product], surfacing [N] usability issues `[NEED DATA]` and turning them into [change] that [outcome]."

## Quality checks before delivering
Every claim still true; every inserted metric sourced or `[NEED DATA]`; ATS readability preserved; human readability preserved; each change tied to a vacancy or market signal. A review that fabricates a metric or flattens everything into generic corporate voice has failed, however polished.
