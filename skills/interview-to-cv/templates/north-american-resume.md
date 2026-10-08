# Template family: North American resume

Markets: `us-en`, `ca-en`, `ca-fr` (Québec). Same structure everywhere; the market file supplies the language, section names, date format, spelling and constraints.

How to use this file:

1. Apply the market filter (`markets/<code>.md`) to the master profile: drop omitted fields, apply transforms.
2. If a job posting was given, run job selection: pick and reorder roles, bullets and skills by relevance.
3. Fill the skeleton below. `{{…}}` are master-profile paths; `[[…]]` are section names taken from the market file's `section_names`.
4. Run the ATS check (DESIGN §11) and the market constraints before handing the result back.

## Conventions shared by the family

- **No personal data beyond contact details.** No photo, date of birth, age, gender, marital status, nationality, dependants or national ID. Markets cannot re-enable them.
- **Reverse-chronological.** Most recent role first. A combination layout (skills block before experience) is allowed for career changers; ask before using it.
- **Achievement bullets.** Start with a strong verb, past tense for past roles, present tense for the current one; no first-person pronouns; quantify where possible.
- **Header:** name, then one contact line. City and province/state only — never a street address.
- **Work authorization** goes in the header contact line or the summary only when the market file says so and the master profile has a value that helps (e.g. permanent resident in Canada).
- **References** are not listed and "References available upon request" is not written.
- **One column, standard headings.** The built-in layout is already ATS-safe; the ATS layout only removes the remaining emphasis (bold company line, separators).

## Resume skeleton

```markdown
# {{name.given}} {{name.family}}

{{contact.city}}, {{contact.region}} · {{contact.phone}} · {{contact.email}} · {{contact.links.linkedin}} · {{contact.links.github}}
<!-- optional, per market: · {{work_authorization.<market>.status | localised}} -->

## [[summary]]

{{summary | localised, 2–4 lines, tailored to the job if given}}

## [[skills]]

- **{{skill group}}:** {{skills, most relevant first}}
<!-- repeat for 3–5 groups; drop levels and years unless the market file keeps them -->

## [[experience]]

### {{role.equivalences.<market>.chosen}} — {{role.company}}
{{role.location | city, region/country}} · {{role.start | date}} – {{role.end | date}}

- {{bullet}}
<!-- bullets per role and years shown come from the market constraints -->

## [[education]]

### {{degree.equivalences.<market>.chosen}} — {{degree.institution}}
{{degree.location | city, country}} · {{degree.end | year}}
<!-- original degree name in parentheses when the equivalent differs: (Ingeniero en Sistemas de Información) -->
<!-- add "Credential assessed by {{assessment.organisation}}" when an assessment exists and the market file says to show it -->

## [[certifications]]

- {{cert.name}} — {{cert.issuer}}, {{cert.issued | year}}

## [[languages]]
<!-- only when a language is relevant to the job or the market (always for ca-en / ca-fr: English and French) -->
- {{language | localised}}: {{level | market transform}}

## [[projects]]
<!-- optional: only with evidence relevant to the job, or for early-career profiles -->
```

### Length

The market file sets the page limit. When the content is over the limit, cut in this order: oldest roles' bullets → optional sections → skills groups → summary length. Never cut the most recent role below three bullets.

## Cover letter skeleton

Called *cover letter* in `us-en` and `ca-en`, *lettre de présentation* in `ca-fr` (Québec usage; *lettre de motivation* is the European term). One page, three to four paragraphs, same header as the resume.

`<<…>>` are **evidence slots**. An empty slot is asked during the interview or flagged in the output — never filled with generic text.

```markdown
{{name.given}} {{name.family}}
{{contact.city}}, {{contact.region}} · {{contact.phone}} · {{contact.email}}

{{date | market format}}

{{hiring manager name, or "Hiring Team"}}
{{company}}

[[salutation]] {{hiring manager name | "Hiring Team"}},

<<Why this company: one specific, verifiable fact about the company — product, launch, engineering blog post, value — and why it matters to the applicant.>>
I am applying for the {{job.title}} position{{, referred by <<referrer name>> | for referral letters}}.

<<Evidence for requirement 1: a quantified achievement from the master profile that maps to the job's top must-have.>>
<<Evidence for requirement 2: a second achievement mapped to another must-have.>>

<<Why here: relocation letters — why this country/city and the work authorization status; career-change letters — what transfers from the previous field.>>

[[closing sentence: availability for an interview, no clichés]]

[[sign-off]]
{{name.given}} {{name.family}}
```

Letter types (DESIGN §9) change only the first and third paragraphs:

| Type | First paragraph | Third paragraph |
|---|---|---|
| Job posting | company fact + position | why here (optional) |
| Unsolicited | company fact + the kind of role sought | what the applicant would bring to a named team |
| Referral | referrer's name in the first sentence | why here (optional) |
| Career change | company fact + position | transferable evidence from the previous field |
| Relocation | company fact + position | why this country/city + work authorization |

Every letter ships with the review warning, the generic-language check, the per-paragraph "could this be sent to any company?" check and the review checklist (DESIGN §9).
