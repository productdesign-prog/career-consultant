# Career Consultant — Claude Cowork plugin

A personal career consultant for Claude Cowork. It interviews you about who you are and what you're looking for, then helps you analyze the job market, score real vacancies against your profile, review and rewrite your resume (market-fit + ATS), write tight cover letters, and track applications.

It works as a pipeline, not a text generator: **market → vacancy → profile → resume → ATS → cover letter → action.** It filters out weak matches, shows its reasoning, demands evidence, states confidence, never auto-submits applications, and never invents experience or metrics.

## Skills

| Skill | What it does |
|---|---|
| `career-consultant` | Intake interview, sets up working files, routes to the rest |
| `career-strategist` | Which roles to target — offer probability, comp, hiring speed, trajectory |
| `market-analyst` | Scans recent real vacancies → Market Requirements Report with frequency % |
| `job-match-scorer` | Weighted 0–100 score + confidence + requirement→evidence map, applies hard-stops |
| `resume-ats-reviewer` | Reviews a resume in two lenses: market-fit (with evidence map) and ATS parseability |
| `resume-rewriter` | Rewrites bullets to a target without inventing experience; Master → Target → Variant |
| `cover-letter-writer` | Short, specific cover letters with a built-in anti-cliché list |
| `career-tracker` | Maintains a vacancy tracker (local spreadsheet or a connected tool) |
| `rejection-analyst` | Turns rejections + feedback into profile/strategy updates |

---

## Install

The address to share with anyone is just this one line:

```
productdesign-prog/career-consultant
```

### Fastest — anyone, no admin needed (Cowork desktop)

1. Open **Personal plugins** → click **+** → **Add marketplace**.
2. Paste: `productdesign-prog/career-consultant`
3. The `career-consultant` plugin appears in the catalog → click **Install**.

That's it — no organization owner required.

### Claude Code (terminal) — two commands

```
/plugin marketplace add productdesign-prog/career-consultant
/plugin install career-consultant@career-consultant
```

Update later with `/plugin marketplace update`.

### Org-wide (optional — organization owner, one-click for everyone)

1. **Organization settings → Plugins → Add plugin → GitHub**.
2. Repository: `productdesign-prog/career-consultant`.
3. Set the install preference: **Available** (self-service), **Installed by default**, or **Required**.
4. (Optional) Enable **Sync automatically** so pushes to this repo roll out on their own.

### Manual file

Build a `.plugin` from the `career-consultant/` folder and upload it in Cowork (**Plugins → upload**).

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
