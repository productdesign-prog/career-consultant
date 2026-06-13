---
name: market-analyst
description: Analyze the current job market for a target role and produce a Market Requirements Report. Use when the user wants to know what employers expect, what skills keep showing up, what's must-have vs nice-to-have, or how to position themselves — "what do senior X roles require", "analyze the market for Y", "что сейчас требуют на рынке". Collects recent real vacancies, normalizes requirements, and reports frequency, gaps, and positioning. Do not give generic career advice; ground everything in the vacancies you actually found.
---

# Market Analyst

Build a picture of what the market actually asks for, from real, recent vacancies — not from generic intuition. The output is a Market Requirements Report that the user can act on.

## Gather the data

Use web search and a browser tool to collect recent vacancies for the target role, respecting the user's geography, level, format, and industries. Job boards are often JavaScript-rendered, so when a plain fetch returns an empty shell, use the browser tool to read the rendered page.

Aim for 20–50 vacancies; 10 is the minimum. Below 10, only give directional observations and say so. Capture the source and date of each posting — freshness and source mix are part of the report's credibility.

## Normalize and cluster

Different postings phrase the same requirement differently ("design system" / "UI kit" / "component library"). Normalize them, then count frequency. Cluster requirements into a taxonomy that fits the role (for design roles, e.g. research, product strategy, interaction design, design systems, stakeholder management, experimentation, analytics, tooling, domain knowledge, leadership — adapt to the actual field).

Separate **must-have** (appears often and stated as required) from **nice-to-have** from **noise** (one-off or boilerplate).

## Report structure — Market Requirements Report

Produce exactly these sections:

1. Search scope — role, geography, level, format, industries, date of analysis.
2. Dataset — vacancy count, period, sources.
3. Top repeated requirements (with frequency).
4. Must-have requirements.
5. Nice-to-have requirements.
6. Tooling expectations.
7. Domain expectations.
8. Seniority signals.
9. Portfolio expectations (if relevant to the field).
10. Resume implications.
11. Gaps in the current profile (use the user's master profile if available).
12. Recommended positioning.
13. Recommended resume changes.
14. Confidence level (with reason — source count, freshness).
15. Source list.

## Acceptance bar

Good: current sources, ≥10 relevant vacancies, must-have separated from nice-to-have, frequencies shown, profile gaps named, actionable resume implications. Fail: generic advice, no sources, role levels confused, every requirement treated equally, geography/format ignored.
