# Career Consultant — Claude Cowork plugin

A personal career consultant for Claude Cowork. It interviews you about who you are and what you're looking for, then helps you analyze the job market, score real vacancies against your profile, review and rewrite your resume (market-fit + ATS), write tight cover letters, and track applications.

It works as a pipeline, not a text generator: **market → vacancy → profile → resume → ATS → cover letter → action.** It filters out weak matches, shows its reasoning, demands evidence, states confidence, never auto-submits applications, and never invents experience or metrics.

## Skills

| Skill | What it does |
|---|---|
| `career-consultant` | Intake interview, sets up working files, routes to the rest |
| `market-analyst` | Scans recent real vacancies → Market Requirements Report |
| `job-match-scorer` | Scores a vacancy 0–100, applies hard-stops, decides apply/maybe/reject |
| `resume-ats-reviewer` | Reviews a resume in two lenses: market-fit and ATS parseability |
| `resume-rewriter` | Rewrites bullets/sections to a target — without inventing experience |
| `cover-letter-writer` | Short, specific cover letters with a built-in anti-cliché list |
| `career-tracker` | Maintains a vacancy tracker (local spreadsheet or a connected tool) |

---

## Install

### Option A — Organization marketplace (recommended, one-click for colleagues)

An **organization owner** does this once:

1. Open **Organization settings → Plugins**.
2. Click **Add plugin** → choose **GitHub** as the source.
3. Enter the repository: `productdesign-prog/career-consultant`
4. Set the install preference for the `career-consultant` plugin:
   - **Available** — colleagues install it themselves in one click from the plugin catalog
   - **Installed by default** — added automatically for everyone (they can remove it)
   - **Required** — installed for everyone, cannot be removed
5. (Optional) Enable **Sync automatically** so updates pushed to this repo roll out on their own.

Colleagues then open the plugin catalog in Cowork and click **Install** — no files to pass around.

### Option B — Claude Code / CLI

```
/plugin marketplace add productdesign-prog/career-consultant
/plugin install career-consultant@career-consultant
```

Update later with `/plugin marketplace update`.

### Option C — Manual file

Build a `.plugin` file from the `career-consultant/` folder and upload it in Cowork (**Plugins → upload**). Useful when you're not an org owner.

---

## Use

After installing, start a chat and say *"help me find a job"* or *"review my resume"* (works in Russian too: *«помоги с поиском работы»*, *«посмотри моё резюме»*). The consultant runs a short intake interview, then helps step by step.

Application packages (tailored resume + cover letter) are only produced for vacancies that score **≥ 80 with no hard-stop**, and only after you confirm.

## What it needs

Adapts to what's available: web search and a browser tool for the market scan, file tools for reading resumes (PDF/DOCX/DOC), and optionally a spreadsheet/notes/database connector for the tracker. See `career-consultant/CONNECTORS.md`.

## Repository layout

```
.claude-plugin/marketplace.json   # marketplace catalog
career-consultant/                # the plugin
  .claude-plugin/plugin.json
  skills/...
  README.md
  CONNECTORS.md
```
