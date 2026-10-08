---
name: interview-to-cv
description: Build and maintain country-adapted CVs/resumes and cover letters by interviewing the user one question at a time, each with a recommended answer. Use this skill whenever the user wants to write, rewrite, translate, update or tailor a CV, resume, curriculum vitae, cover letter, covering letter, lettre de motivation or carta de presentación — especially for job applications abroad or in several countries (US, Canada, Québec, UK, Australia, France, Belgium, Latin America), when they paste a job posting to apply to, ask for an ATS-friendly resume, want their CV in a specific template, or need to know how a job title or degree translates to another country. Also use it for quick updates such as "add my new job/certification to my CV".
---

# Interview to CV

Builds one **master profile** of the user by interviewing them, then generates a CV (and cover letters) per target market:

```
master profile  ×  market filter  ×  job selection (optional)  ×  layout
```

All paths below are relative to this skill's folder unless they start with `my-cv/`.

## Files

| File | Read it when |
|---|---|
| `master/schema.md` | Creating or editing the master profile. |
| `markets/<code>.md` | Generating for that market, or asking market-specific questions. |
| `templates/<family>.md` | Generating a CV or cover letter for a market of that family (named in the market file's `template`). |
| `references/equivalences.md` | Resolving a job title or degree for a market. |
| `references/classifications.md` | Citing a classification version. |
| `locales/<lang>/questions.md` | Interviewing. |
| `locales/<lang>/messages.md` | Showing a fixed message (warnings, checklists, disclaimers). |
| `locales/<lang>/generic-phrases.md` | Checking a summary or cover letter. |
| `workflows/<feature>.md` | Running that feature (see Modes and Generate). |

Read only the files the current step needs. Market and template files are long; load one market at a time.

Available markets:

| Code | Market | Template |
|---|---|---|
| `us-en` | United States | `north-american-resume` |
| `ca-en` | Canada (English) | `north-american-resume` |
| `ca-fr` | Québec (French) | `north-american-resume` |
| `uk-en` | United Kingdom | `commonwealth-cv` |
| `au-en` | Australia | `commonwealth-cv` |
| `fr-fr` | France | `french-european-cv` |
| `be-fr` | Belgium (French) | `french-european-cv` |
| `latam-es` | Latin America (Spanish) | `latam-cv` |

## Languages

- **Interface language** (`interface_language`): the language of the conversation and of everything in `locales/`. Default to the language the user writes in; if `locales/<lang>/` does not exist, use `en` and translate on the fly, keeping the meaning of `messages.md` texts intact.
- **Output language**: set by each market (`language` in the market file). A Spanish-speaking user can be interviewed in Spanish and get a Québec CV in French.

## Where the user's data lives

```
my-cv/
├── master.md
├── markets/<code>/cv.md
├── templates/custom/
├── letters/<yyyy-mm>-<company>.md        # letters not tied to a posting
└── applications/<yyyy-mm>-<company>-<role>/
    ├── job.md
    ├── cv.md
    └── cover-letter.md
```

- **With a file system** (Claude Code, Cowork): look for `my-cv/` in the working directory. Create it if missing. Show `messages.md#privacy.folder` the first time, and check that `my-cv/` is not tracked by a public git repository; warn if it is.
- **Without persistent files** (Claude.ai): ask the user to attach their `master.md` (or the zip) if they have one. At the end of every session hand back the updated `master.md` — or the whole folder zipped — and show `messages.md#privacy.claude_ai`.

## Start of every session

1. Load the master profile if it exists.
2. If both `last_updated` and `last_checked` are older than **3 months**, ask `questions.md#update.what` before anything else.
3. If `outputs` lists files generated before `last_updated`, mention them with `messages.md#generate.stale`.
4. Work out what the user wants and go to the matching mode.

## Modes

| The user wants to… | Do |
|---|---|
| Create a CV / start from scratch / "here is my CV" | Intake → Interview → Equivalences → Generate |
| Get a CV for another country | Interview (only the new market's questions) → Equivalences → Generate |
| Know how a title or degree translates | Equivalences only, for the requested market; offer to save the result |
| Add or change one thing ("new job", "got a certification", "moved") | `workflows/quick-update.md` |
| Write a cover letter (any type) | `workflows/cover-letter.md` |
| Fill their own template / an application form | `workflows/custom-templates.md` |
| Apply to a job / "here is a posting" / "how well do I match?" | `workflows/job-tailoring.md` (needs a master profile; run Intake + Interview first if missing) |

## 1. Intake

1. If the user provides a CV (text, PDF, DOCX, LinkedIn export), extract everything into the master profile following `master/schema.md`. Keep original job titles and degree names in `original_title` / `original_degree`; write free text in English.
2. Never guess missing facts. Leave fields absent so the interview asks for them.
3. Show a short summary of what was captured (roles, degrees, languages) and what is missing, then start the interview.

## 2. Interview

Follow `locales/<lang>/questions.md`.

- **One question per message**, always with a recommended answer the user can accept with "ok".
- **Never ask what is already known.** Skip any question whose field is set or `declined`.
- Ask only what the target markets need: personal data only when a market's **Include** list uses it, credential questions only for markets with a `credential_recognition` block.
- Ask for numbers on achievements, but never invent them; an estimate must be marked as approximate by the user.
- Save each answer to the master profile as soon as it is given (bump `last_updated`), so stopping halfway loses nothing.
- Show `messages.md#interview.progress` every 5 questions or so.

## 3. Equivalences

For every role in the last 15 years and every degree, for every target market without a cached entry, follow `references/equivalences.md`: 2–3 options, recommended first, each with its code and source; the user chooses; save the result. An official credential assessment overrides any lookup. Show `messages.md#equivalence.disclaimer` the first time.

## 4. Generate

For each target market:

1. **Freshness.** If the market file's `last_verified` is older than 6 months, show `messages.md#freshness.market` and offer to re-check its sources before generating.
2. **Filter.** Apply the market file: drop everything in **Omit** and anything not in **Include**; apply every **Transform** row.
3. **Layout.** Fill the family template's skeleton with the filtered profile and the market's `section_names`.
4. **Constraints.** Enforce length, years shown and bullets per role, cutting in the order the template gives. Never cut content the user flagged as essential without asking.
5. **ATS check.** Run `workflows/ats-check.md` and fix what can be fixed without new facts.
6. **Write** `my-cv/markets/<code>/cv.md`, record it in `outputs`, and show `messages.md#generate.done` with the ATS result.

Generated text never adds facts that are not in the master profile.

## Rules that always apply

- Fictional examples only in anything shown as an example; never reuse another user's data.
- Data a market file lists under **Omit** stays out by default. If the user asks to include it, explain the risk in that market (and the legal reason when the market file gives one) and include it only after they confirm.
- Protected titles in the market file (e.g. "Engineer" in Canada) are never used without the licence they require.
- Institutions, companies, products and certifications are never translated.
- When a source or rule is uncertain, say so instead of presenting it as fact.
