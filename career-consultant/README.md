# Career Consultant

A personal career consultant you can install and share. It interviews you about who you are and what you're looking for, then helps you analyze the job market, score real vacancies against your profile, review and rewrite your resume (market-fit + ATS), write tight cover letters, and track your applications.

It works as a pipeline, not a text generator: **market → vacancy → profile → resume → ATS → cover letter → action.** It filters out weak matches, shows its reasoning, demands evidence, and states confidence. It never guarantees employment, never auto-submits applications, and never invents experience, metrics, titles, or companies.

## How to use it

1. Install the plugin.
2. Start a chat and say something like *"help me find a job"* or *"review my resume"*. The consultant runs a short intake interview (resume, target roles, geography, languages, work format, constraints, achievements).
3. From there, ask for what you need — a market scan, a vacancy score, a resume review, a cover letter, or a tracker.

Application packages (tailored resume + cover letter) are only produced for vacancies that score **≥ 80 with no hard-stop**, and only after you confirm.

## Skills

| Skill | What it does |
|---|---|
| `career-consultant` | Front door: intake interview, sets up your working files, routes to the rest |
| `market-analyst` | Scans recent real vacancies → Market Requirements Report |
| `job-match-scorer` | Scores a vacancy 0–100, applies hard-stops, decides apply/maybe/reject |
| `resume-ats-reviewer` | Reviews a resume in two lenses: market-fit and ATS parseability |
| `resume-rewriter` | Rewrites bullets/sections to a target — without inventing experience |
| `cover-letter-writer` | Short, specific cover letters with a built-in anti-cliché ("stop-slop") list |
| `career-tracker` | Maintains a vacancy tracker (local spreadsheet, or a connected tool) |

## What it needs

Useful capabilities (the consultant adapts to what's available): web search and a browser tool for the market scan and company research; file tools for reading resumes (PDF/DOCX/DOC); and optionally a spreadsheet/notes/database connector for the tracker. See `CONNECTORS.md`.

## Principles

Evidence or it doesn't count · truth over optimization · no slop · confidence on every output · report source count and freshness.
