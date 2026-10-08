# Workflow: custom templates

The user brings their own format — a company's application form, a recruiter's template, a design they like — and the skill fills it from the master profile (DESIGN §12).

## 1. Receive the template

Accepted: Markdown, Word (`.docx`), fillable PDF (AcroForm fields), plain text, or a pasted structure. For a non-fillable PDF or an image, offer to recreate its structure as Markdown or Word, and say the original design cannot be filled in place.

Ask, with a recommended answer:

- the **target market** (decides language, omitted data and equivalences);
- whether it is for a **specific job** (then run the job analysis from `workflows/job-tailoring.md` first);
- a **name** to save it under.

Save the original in `my-cv/templates/custom/<name>/` and keep it unchanged.

## 2. Map fields

Read every field, placeholder, heading and table cell. Map each one to a master-profile path (`master/schema.md`) and show the mapping before filling:

```
Template field                 → Master profile
"Full name"                    → name.given + name.family
"Current position"             → most recent role: equivalences.<market>.chosen
"Years of experience in Java"  → computed from roles whose stack includes Java (6) — please confirm
"Date of birth"                → personal.date_of_birth — omitted by default in this market (see note)
"Why do you want to join?"     → no match — I'll ask you
```

Rules:

- A field that asks for data the market file lists under **Omit** is left empty by default; tell the user it is optional in that market and ask whether they want to fill it (`SKILL.md`, rules).
- Computed values (years of experience, number of projects) are shown with how they were computed and confirmed by the user.
- Fields with length limits (characters, words, lines) are respected; shorten from the master content, never cut mid-sentence.

## 3. Mini-interview

Ask only for fields with no match, one at a time with a recommended answer (DESIGN §12). Save every answer that is a fact about the user to the master profile, so the next template or market can reuse it; answers specific to this template (e.g. "Why do you want to join us?") are saved with the filled template only.

## 4. Select and fill

- With a job: select and order content as in job tailoring step 5.
- Without a job: use the most recent and strongest content, within the template's space.
- Keep the template's own design, fonts and layout. Do not restyle it.
- Equivalences come from the master profile cache; resolve missing ones first (`references/equivalences.md`).

## 5. Check and deliver

1. Run the ATS check (`workflows/ats-check.md`) when the template will be uploaded to a job portal; report layout issues (columns, tables) as warnings — the user chose the design.
2. List empty fields and why they are empty.
3. Save the filled file next to the original: `my-cv/templates/custom/<name>/filled-<yyyy-mm-dd>.<ext>` (or inside the application folder when tied to a job). For Word and PDF output, use the export workflow's tooling.
4. Record the template in the master profile's `outputs` so later changes can mark it stale.

## Reuse

The next time the user asks for "my <name> template", reuse the saved mapping (`my-cv/templates/custom/<name>/mapping.md`) and only ask for fields that changed.
