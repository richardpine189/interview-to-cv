# Interview to CV

**Answer a few questions. Get a CV for every country.**

`interview-to-cv` is an agent skill for Claude that builds your CV by *interviewing* you — one question at a time, always with a recommended answer — and then generates versions adapted to the hiring standards of each target market, in the right language.

> Status: 🚧 v1 under construction.

## What makes it different

- **Interview, not a form.** Bring your current CV (or nothing). The skill only asks what it doesn't already know.
- **One master profile, many markets.** Everything about you lives in a single master file. Each market applies its own filters: what to include, what to omit, how to format it.
- **Real equivalences.** Job titles and degrees are mapped to their local equivalents using official classifications (ISCO, O\*NET, NOC, SOC, OSCA, ESCO, ROME, ISCED), with sources and dates.
- **Credential recognition guidance.** Asks whether you have a formal assessment (e.g. an ECA for Canada) and points you to the official process if you don't.
- **Cover letters that aren't generic.** Every letter comes with a mandatory review warning and a generic-language check.
- **Job matching.** Paste a job posting to get a match score, gaps, and a tailored CV.
- **Your own templates.** Bring any format and the skill fills it from your master profile.
- **Export your way.** Markdown, Word, PDF, ATS-safe, XeLaTeX or Europass.

## Markets (v1)

| Family | Markets | Language |
|---|---|---|
| North American resume | United States, Canada (EN), Québec | English / French |
| Commonwealth CV | United Kingdom, Australia | English |
| French-European CV | France, Belgium | French |
| Latin American CV | Latin America | Spanish |

## Install

```bash
npx skills add richardpine189/interview-to-cv
```

Or download the `.skill` file from Releases and upload it in Claude.ai.

## Your data stays yours

Your master profile contains personal data (date of birth, nationality, immigration status…). Keep your `my-cv/` folder private and **never** commit it to a public repository. This repo only contains fictional examples.

## Roadmap

- LinkedIn profile per language, generated from the master profile
- Interview preparation (STAR stories) from your CV
- More markets: Germany, Brazil, Portugal…
- Interface translations: Spanish, French, German, Portuguese

## License

MIT
