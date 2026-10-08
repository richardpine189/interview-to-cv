# Template family: French-European CV

Markets: `fr-fr` (France), `be-fr` (Belgium, French-speaking). Output in French; the market file supplies vocabulary, section names and constraints.

How to use this file:

1. Apply the market filter (`markets/<code>.md`) to the master profile.
2. If a job posting was given, run job selection.
3. Fill the skeleton below. `{{…}}` are master-profile paths; `[[…]]` are section names from the market file's `section_names`.
4. Run the ATS check and the market constraints.

## Conventions shared by the family

- **CV title (titre du CV):** a one-line headline under the name stating the target job, optionally with one strength (« Développeur backend Go — 9 ans d'expérience en paiements »). Always present.
- **Personal data:** name and contact details only, by default. No date of birth, age, marital status, nationality or gender. A photo is never added by default; the market file says whether it may be offered.
- **Order:** experience before education for experienced profiles; education first for students and recent graduates.
- **Bullets:** action nouns or verbs in the infinitive or past tense (« Conception et déploiement… », « Réduire… »), no first person; quantified where possible.
- **Languages** always get their own section, with CEFR levels (*CECR / CECRL*) — recruiters in both markets read them.
- **Centres d'intérêt** (interests) are accepted at the end; keep them short and specific, or omit them.
- **One column, standard headings** — ATS-safe. Europass is offered as an export format, not as the default layout.

## CV skeleton

```markdown
# {{name.given}} {{name.family | UPPERCASE family name is common: Alex EXAMPLE}}

**{{CV title: target job — key strength}}**

{{contact.city}} · {{contact.phone | international format}} · {{contact.email}} · {{contact.links.linkedin}} · {{contact.links.github}}
<!-- optional: · {{work_authorization.<market>.status | localised}} -->

## [[profile]]
<!-- optional: 2–3 lines; recommended for international and career-change profiles -->

## [[experience]]

### {{role.equivalences.<market>.chosen}} — {{role.company}}, {{role.location | ville, pays}}
{{role.start | date}} – {{role.end | date}}

- {{bullet}}

## [[education]]

### {{degree.equivalences.<market>.chosen}} — {{degree.institution}}, {{degree.location | pays}}
{{degree.end | année}}
<!-- original degree name in parentheses when the equivalent differs; add the comparability attestation when it exists -->

## [[skills]]

- **{{skill group}} :** {{skills, most relevant first}}

## [[languages]]

- {{language | localised}} : {{level | market transform}}

## [[certifications]]

- {{cert.name}} — {{cert.issuer}}, {{cert.issued | année}}

## [[interests]]
<!-- optional, 1 line -->
```

French typography: a non-breaking space before `:`, `;`, `?`, `!` and inside `« »`.

### Length

Set by the market file. When over the limit, cut in this order: interests → oldest roles' bullets → certifications not relevant to the job → skills groups → profile.

## Cover letter skeleton (lettre de motivation)

One page, three or four paragraphs, a formal register. The classic French structure is **vous – moi – nous**: what the company is doing (vous), what the applicant brings (moi), what they will do together (nous). `<<…>>` are evidence slots: asked or flagged, never padded.

```markdown
{{name.given}} {{name.family}}
{{contact.city}}
{{contact.phone}} · {{contact.email}}

{{company}}
{{hiring manager name and title, if known}}
{{company city}}

{{city}}, le {{date | 7 octobre 2026}}

**Objet : candidature au poste de {{job.title}}{{ — réf. job.reference | if any}}**

[[salutation]]

<<Vous : one specific, verifiable fact about the company (project, product, growth, value) and why it matters to the applicant.>>

<<Moi : one or two quantified achievements mapped to the main requirements of the posting.>>

<<Nous : what the applicant proposes to contribute in the first months; for relocation, why this country/city and the right to work.>>

[[closing: request for an interview]]

[[formule de politesse]]

{{name.given}} {{name.family}}
```

Letter types (job posting, *candidature spontanée*, referral, career change, relocation) change only the *vous* and *nous* paragraphs. Every letter ships with the review warning, the generic-language check, the per-paragraph "could this be sent to any company?" check and the review checklist.
