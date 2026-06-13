---
name: career-tracker
description: Create and maintain a job-application tracker. Use when the user wants to track vacancies, applications, statuses, or decisions — "set up a job tracker", "log this vacancy", "update the status", "веди таблицу вакансий". Maintains a consistent schema and status set, records the match score and decision rationale, and links resume/cover-letter versions. Picks the best available storage: a local spreadsheet by default, or Google Sheets / Notion / Airtable if a connector is available.
---

# Career Tracker

Keep one source of truth for the user's job search: what was found, how it scored, what was decided and why, and what happens next.

## Storage

Pick based on what's connected. Default to a local spreadsheet (`.xlsx`/`.csv`) in the user's folder — it always works. If the user has a connected spreadsheet/notes/database tool (e.g. Google Sheets via Drive, Notion, or Airtable), offer to use that instead and create the tracker there. Don't assume a specific product; ask or detect.

## Schema (columns)

ID · Date found · Company · Role · Link · Source · Location · Work format · Salary · Level · Industry · Match score · Decision · Hard-stop? · Main fit reason · Main risk · Resume version · Cover letter version · Status · Date applied · Response · Interview stage · Feedback · Next action · Notes.

## Statuses

New · Parsed · Rejected · Maybe · Ready to apply · Applied · Recruiter screen · Interview · Test task · Offer · Rejected by company · Withdrawn.

## Behavior

- On a new vacancy: add a row with status New/Parsed and capture source + date.
- After `job-match-scorer`: write the score, decision, hard-stop flag, main fit reason, and main risk.
- Only set "Ready to apply" for vacancies at match ≥ 80 with no hard-stop.
- When the user applies: record date, the resume and cover-letter versions sent.
- Track outcomes (response, interview stage, feedback, rejection reason) so patterns become visible over time.
- Keep the decision rationale in the row — future-you should understand past decisions without re-reading the posting.

## Weekly view (optional)

On request, summarize the tracker into a short weekly report: new vacancies, what passed the threshold, what's awaiting action, and the next 3–5 moves.
