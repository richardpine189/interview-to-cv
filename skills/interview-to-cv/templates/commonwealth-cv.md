# Template family: Commonwealth CV

Markets: `uk-en`, `au-en`. Called a **CV** in the UK and a **résumé / CV** in Australia; same structure. The market file supplies spelling, section names, length and the references rule.

How to use this file:

1. Apply the market filter (`markets/<code>.md`) to the master profile.
2. If a job posting was given, run job selection.
3. Fill the skeleton below. `{{…}}` are master-profile paths; `[[…]]` are section names from the market file's `section_names`.
4. Run the ATS check and the market constraints.

## Conventions shared by the family

- **No photo, date of birth, age, gender, marital status, nationality or dependants.** Markets cannot re-enable them.
- **Personal statement / profile** of 3–5 lines under the header: who the user is, what they want, why they fit. Written without "I" in the UK convention ("Backend developer with…"), first person accepted in Australia.
- **Reverse-chronological.** Most recent role first. Early-career users put education before experience.
- **Achievement bullets** in past tense for past roles, present tense for the current role; quantified where possible.
- **Key skills** block near the top, matched to the job.
- **Right to work** stated in the header or profile when the master profile has a value that needs no sponsorship.
- **References** follow the market rule: a "References available on request" line (UK) or two named referees (Australia, when the user has consent).
- **One column, standard headings** — already ATS-safe.

## CV skeleton

```markdown
# {{name.given}} {{name.family}}

{{contact.city}} · {{contact.phone}} · {{contact.email}} · {{contact.links.linkedin}} · {{contact.links.github}}
<!-- optional: · {{work_authorization.<market>.status | localised}} -->

## [[profile]]

{{summary | localised, 3–5 lines, tailored to the job if given}}

## [[key_skills]]

- **{{skill group}}:** {{skills, most relevant first}}

## [[experience]]

### {{role.equivalences.<market>.chosen}} — {{role.company}}, {{role.location | city, country}}
{{role.start | date}} – {{role.end | date}}

- {{bullet}}

## [[education]]

### {{degree.equivalences.<market>.chosen}} — {{degree.institution}}, {{degree.location | country}}
{{degree.end | year}}
<!-- original degree name in parentheses when the equivalent differs -->
<!-- "Comparability confirmed by {{assessment.organisation}}" when an assessment exists and the market file says to show it -->

## [[certifications]]

- {{cert.name}} — {{cert.issuer}}, {{cert.issued | year}}

## [[languages]]
<!-- only when relevant to the job or above B2 -->
- {{language | localised}}: {{level | market transform}}

## [[references]]
<!-- uk-en: one line "Available on request". au-en: two referees with consent, or "Available on request". -->
```

### Length

Set by the market file. When over the limit, cut in this order: oldest roles' bullets → languages and certifications not relevant to the job → skills groups → profile length. Never cut the most recent role below three bullets.

## Cover letter skeleton

Called a **covering letter** in the UK (*cover letter* is also understood) and a **cover letter** in Australia. One page, three to five paragraphs. `<<…>>` are evidence slots: asked or flagged, never padded.

```markdown
{{name.given}} {{name.family}}
{{contact.city}} · {{contact.phone}} · {{contact.email}}

{{date | market format}}

{{hiring manager name, or "Hiring Manager"}}
{{company}}

[[salutation]] {{hiring manager name | "Hiring Manager"}},

**Re: {{job.title}}{{, ref. job.reference | if the posting has one}}**

<<Why this company: one specific, verifiable fact about the company and why it matters to the applicant.>>

<<Evidence for the top requirement: a quantified achievement mapped to it.>>
<<Evidence for a second requirement, or for a selection criterion (Australia: address each key criterion the posting lists).>>

<<Why here: relocation — why this country/city and the right to work or visa route; career change — what transfers.>>

[[closing sentence]]

[[sign-off]]
{{name.given}} {{name.family}}
```

Sign-off follows the salutation: a named person → *Yours sincerely*; *Dear Hiring Manager* → *Yours faithfully* (UK) or *Kind regards* (Australia). The market file holds the exact values.

Letter types (job posting, unsolicited, referral, career change, relocation) change only the first and fourth paragraphs, as in the North American family. Every letter ships with the review warning, the generic-language check, the per-paragraph "could this be sent to any company?" check and the review checklist.
