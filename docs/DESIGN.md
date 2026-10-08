# interview-to-cv — Design (v1)

This document records the design decisions behind the skill. It was produced through an interview ("grilling") session and should be updated whenever a decision changes.

## 1. Purpose

Build country-adapted CVs and cover letters for IT professionals by interviewing the user, then generating one version per target market and language.

## 2. Core model

Every output is the composition of four pieces:

```
master profile  ×  market filter  ×  job selection (optional)  ×  layout
```

- **Master profile** — a superset of everything about the user, written once.
- **Market filter** — per-country rules: include / omit / transform / constrain.
- **Job selection** — optional: picks and reorders the master content that best fits a job posting.
- **Layout** — a built-in template family, the ATS layout, or a user-supplied custom template.

## 3. Flow

1. **Intake** — read the user's existing CV (if any) and convert it into the master profile.
2. **Interview** — ask one question at a time, each with a recommended answer. Never ask what is already known.
3. **Equivalence resolution** — map job titles and degrees to each target market.
4. **Generation** — produce Markdown for each market (and per application when a job is provided).
5. **Export** — the user chooses the format; handled by the export sub-skill.

## 4. Language strategy

- Skill instructions and market rules: **English**.
- Everything the user reads (questions, section names, explanations, generic-phrase lists): **`locales/<lang>/`**, so new interface languages are added as folders.
- *Conversation language* and *target market* are independent axes.
- v1 interface locale: `en`. Planned: `es`, `fr`, `de`, `pt`.

## 5. Master profile

- Markdown with YAML front matter for personal data; free sections for the rest.
- Superset: stores data some markets forbid (photo, date of birth, nationality, marital status, visa status per country, CEFR language levels, references…). Market filters decide what reaches each output.
- Canonical language: English. Bilingual fields where literal translation fails:
  - Degrees: original name + equivalent per market.
  - Institutions and companies: never translated.
  - Job titles: original + equivalent per market.
- Resolved equivalences are cached in the master profile with chosen option, rejected alternatives, source and date.

## 6. Markets and template families (v1)

| Family | Template | Markets |
|---|---|---|
| North American resume | `templates/north-american-resume.md` | `us-en`, `ca-en`, `ca-fr` |
| Commonwealth CV | `templates/commonwealth-cv.md` | `uk-en`, `au-en` |
| French-European CV | `templates/french-european-cv.md` | `fr-fr`, `be-fr` |
| Latin American CV | `templates/latam-cv.md` | `latam-es` |

Québec belongs to the North American family (North American conventions, French language).

`latam-es` is a single market for all of Latin America and follows the most conservative convention: no photo and no personal data beyond contact details (no date of birth, national ID, marital status or nationality). The region's hiring practice has moved away from requesting them, so one conservative rule set serves every country.

Each `markets/<code>.md` contains:
- `family`, `language`, `last_verified`
- **include/omit** rules, **transform** rules (dates, spelling, section names, language levels), **constraints** (length, bullets per role, years shown, references)
- **occupation sources** to query first (NOC, O\*NET, SOC, OSCA, ESCO, ROME…)
- **`credential_recognition`** block: organisation(s), official link, purpose, validity, when to ask

## 7. Equivalence resolution

Two separate tracks, each always presenting 2–3 options with a recommended one and its source:

- **Role / job title** — official occupation classification of the target market (ISCO-08 as bridge) + validation against current job postings.
- **Degree / field of study** — ISCED (UNESCO) as bridge + credential evaluator logic (WES, ENIC-NARIC…).

LinkedIn is not used as a data source (no public API; automated scraping is against its terms).

Equivalences are guidance, not formal assessments.

## 8. Credential recognition

The interview asks whether the user holds a formal assessment for each target market where it matters for migration (e.g. Canada ECA, Australia ACS skills assessment for ICT, UK ENIC, ENIC-NARIC France/Belgium).

- **Yes** → record organisation, result, reference number, issue date; the official result overrides looked-up equivalences; warn when it is about to expire.
- **No** → leave a recommendation with the official link so the user can start the process.

## 9. Cover letters

- Types: job posting, unsolicited (*candidature spontanée*), referral, career change, relocation.
- Variants per family (cover letter, covering letter, lettre de motivation FR/BE/QC, carta de presentación).
- Templates use **evidence slots** (something specific about the company, a quantified achievement tied to a requirement, why this country/city) instead of filler phrases. Empty slots are asked or flagged — never padded.
- Every letter ships with:
  1. a fixed warning asking the user to review it twice before sending;
  2. a generic-language check against `locales/<lang>/generic-phrases.md`;
  3. a per-paragraph "could this be sent to any company?" check;
  4. a short review checklist.

## 10. Job tailoring and match score

- Optional mode: the user pastes a job posting.
- Match score as a breakdown: must-haves covered, nice-to-haves covered, keywords, seniority, location/visa. Lists gaps and an application strategy.
- Never invents experience; unsupported requirements are reported, not filled.
- The same job analysis feeds the tailored CV and the cover letter.

## 11. ATS

- **ATS check** on every generated CV: multi-column layouts, tables, data in headers/footers, icons/graphics, non-standard headings, image-only PDFs.
- **ATS layout**: single column, standard headings in the market language, plain structured text.

## 12. Custom templates

- The user provides a template (`.md`, `.docx`, fillable PDF…).
- The skill maps its fields to the master profile, fills what it can, selects the best-fitting content when a job is provided, and runs a mini-interview for missing fields (answers are saved to the master profile).
- Templates are stored in `my-cv/templates/custom/` for reuse.

## 13. Quick update

- "I got the AWS certification", "I changed jobs in August" → the skill asks only the 2–3 missing facts, resolves new equivalences, updates the master profile and lists the outputs that became stale.
- If the master profile has not changed in several months, the skill asks whether there is anything new.

## 14. Export (sub-skill)

The user chooses: Markdown, Word (.docx), PDF, ATS-safe, XeLaTeX (`.tex`, with Overleaf instructions if no local TeX), Europass (format verified against the current Europass platform before implementation). Custom Word/PDF templates keep their own design.

## 15. Freshness

- Every market and reference file carries `last_verified`.
- If older than **6 months**, the skill warns the user and offers to check for changes.
- A scheduled GitHub Action opens a review issue every 6 months.

## 16. User data layout

```
my-cv/
├── master.md
├── markets/<code>/cv.md
├── templates/custom/
├── letters/<yyyy-mm>-<company>.md
└── applications/<yyyy-mm>-<company>-<role>/
    ├── job.md
    ├── cv.md
    └── cover-letter.md
```

- Claude Code: lives on disk; can be versioned in a **private** repo.
- Claude.ai: the skill hands back the updated `master.md` (or the zipped folder) at the end of each session.
- The skill warns that this folder must never be pushed to a public repository.

## 17. Skill file layout

All skill resources live inside the skill folder, because that folder is the only thing installed by `npx skills add` or packaged into the `.skill` file. Paths elsewhere in this document are relative to it.

```
skills/interview-to-cv/
├── SKILL.md
├── master/schema.md
├── templates/<family>.md
├── markets/<code>.md
├── locales/<lang>/
├── references/
└── workflows/<feature>.md
```

`SKILL.md` holds the core flow (intake → interview → equivalences → generation). Each optional feature (job tailoring, cover letters, ATS check, custom templates, quick update, freshness review, export) lives in its own file under `workflows/` and is read only when that feature is used.

## 18. Out of scope for v1 (roadmap)

LinkedIn profile per language · interview preparation (STAR) · new markets (DE, BR, PT…) · interface translations (es, fr, de, pt).
