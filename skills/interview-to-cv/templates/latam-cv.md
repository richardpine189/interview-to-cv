# Template family: Latin American CV

Market: `latam-es` (Spanish-speaking Latin America). Called *currículum (vitae)* or *CV*; *hoja de vida* in Colombia. Neutral Latin American Spanish, adapted to the target country's vocabulary when the user names one.

How to use this file:

1. Apply the market filter (`markets/latam-es.md`) to the master profile.
2. If a job posting was given, run job selection.
3. Fill the skeleton below. `{{…}}` are master-profile paths; `[[…]]` are section names from the market file's `section_names`.
4. Run the ATS check and the market constraints.

## Conventions

- **Conservative personal data (DESIGN §6).** Name and contact details only: no photo, date of birth, age, national ID (DNI, CURP, RUT, cédula), marital status, nationality or gender — even though older CVs in the region included them.
- **Professional profile** of 3–4 lines under the header.
- **Reverse-chronological**, experience before education for experienced profiles.
- **Achievement bullets** with a verb in the past tense for past roles (*Reduje*, *Lideré*) or a noun (*Reducción de…*); first person singular is accepted in the region but the impersonal form reads more professional — follow the market file.
- **Languages** in their own section with level and CEFR code; English level is decisive for most IT roles.
- **One column, standard headings** — ATS-safe.

## CV skeleton

```markdown
# {{name.given}} {{name.family}}

**{{target role — optional headline}}**

{{contact.city}}, {{contact.country}} · {{contact.phone | international format}} · {{contact.email}} · {{contact.links.linkedin}} · {{contact.links.github}}
<!-- optional: · {{work_authorization.latam-es.status | localised}} -->

## [[profile]]

{{summary | localised, 3–4 lines, tailored to the job if given}}

## [[experience]]

### {{role.equivalences.latam-es.chosen}} — {{role.company}}, {{role.location | ciudad, país}}
{{role.start | date}} – {{role.end | date}}

- {{bullet}}

## [[education]]

### {{degree.equivalences.latam-es.chosen}} — {{degree.institution}}, {{degree.location | país}}
{{degree.end | año}}
<!-- original name when the equivalent differs; add the recognition (convalidación / revalidación / reconocimiento) when it exists -->

## [[skills]]

- **{{skill group}}:** {{skills, most relevant first}}

## [[languages]]

- {{language | localised}}: {{level | market transform}}

## [[certifications]]

- {{cert.name}} — {{cert.issuer}}, {{cert.issued | año}}

## [[projects]]
<!-- optional -->
```

### Length

Set by the market file. When over the limit, cut in this order: projects → oldest roles' bullets → certifications not relevant to the job → skills groups → profile.

## Cover letter skeleton (carta de presentación)

One page, three or four paragraphs, formal but direct. `<<…>>` are evidence slots: asked or flagged, never padded.

```markdown
{{name.given}} {{name.family}}
{{contact.city}}, {{contact.country}} · {{contact.phone}} · {{contact.email}}

{{city}}, {{date | 7 de octubre de 2026}}

{{hiring manager name, or "Equipo de Selección"}}
{{company}}

**Ref.: {{job.title}}{{ — job.reference | if any}}**

[[salutation]]

<<Por qué esta empresa: un dato concreto y verificable de la empresa y por qué le importa al postulante.>>

<<Evidencia 1: un logro cuantificado ligado al requisito principal del aviso.>>
<<Evidencia 2: otro logro ligado a otro requisito.>>

<<Por qué aquí: reubicación — por qué este país/ciudad y la situación migratoria; cambio de carrera — qué se transfiere.>>

[[closing]]

[[sign-off]]
{{name.given}} {{name.family}}
```

Letter types (job posting, *postulación espontánea*, referral, career change, relocation) change only the first and last evidence paragraphs. Every letter ships with the review warning, the generic-language check, the per-paragraph "could this be sent to any company?" check and the review checklist.
