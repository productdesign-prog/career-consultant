# Connectors

This plugin is tool-agnostic — it describes workflows by capability, not by a specific product, so each user can connect whatever they have.

## Capabilities the consultant uses

| Capability | Used for | Options |
|---|---|---|
| Web search | Market scan, company research, finding vacancies | built-in web search |
| Browser | Reading JavaScript-rendered job boards (LinkedIn, etc.) | Claude in Chrome / browser tool |
| File reading | Parsing resumes (PDF / DOCX / DOC / RTF) | built-in file tools + pdf/docx skills |
| Tracker storage | The vacancy tracker | local spreadsheet (default), or Google Sheets, Notion, Airtable |
| Email (optional) | Pulling job alerts from the inbox | Gmail or another mail connector |

## Notes

- Nothing is required to get started — with only web search and file tools the consultant can interview you, scan the market, and review a resume.
- The tracker defaults to a local spreadsheet. If you connect Google Sheets / Notion / Airtable, the consultant will offer to use it instead.
- For LinkedIn and similar job boards, a browser tool gives much better results than plain page fetches.
