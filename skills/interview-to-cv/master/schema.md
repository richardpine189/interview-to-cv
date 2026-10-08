# Master profile schema

The master profile (`my-cv/master.md`) is the single source of truth about the user. Every CV, cover letter and custom template is generated from it through a market filter (`markets/<code>.md`) and a layout (`templates/<family>.md`).

Rules:

- **Superset.** Store everything the user is willing to share, including data that some markets forbid (photo, date of birth, marital status…). The market filter decides what reaches each output — never drop a field here because one market omits it.
- **Canonical language: English.** Free text is written in English. Translations are produced at generation time, except for the bilingual fields below.
- **Never translated:** names of companies, institutions, products and certifications.
- **Bilingual fields:** job titles and degrees keep their *original* wording plus one *equivalent* per target market (see [Equivalences](#equivalences)).
- **Unknown ≠ empty.** A field that was asked and declined is `declined`; a field never asked is absent. The interview only asks for absent fields that a target market needs.
- **Dates:** `YYYY-MM` for periods, `YYYY-MM-DD` for exact dates; `present` for ongoing roles.
- **IDs:** every role, degree, certification and project has a stable kebab-case `id` so applications and equivalences can point to it.

The file has two parts: YAML front matter for structured personal data, then Markdown sections for the career content.

---

## 1. Front matter

```yaml
---
schema_version: 1
last_updated: 2026-10-07          # bumped on every change; drives the "anything new?" prompt
interface_language: en            # language of questions and explanations (locales/<lang>/)
target_markets: [us-en, ca-en, ca-fr]

name:
  given: Alex
  family: Example
  preferred: Alex                 # optional, for markets that use a preferred name
pronouns: they/them               # optional; never inferred

contact:
  email: alex.example@example.com
  phone: "+1 555 0100"
  city: Springfield
  region: ON
  country: CA
  willing_to_relocate: true
  links:
    linkedin: https://www.linkedin.com/in/alex-example
    github: https://github.com/alex-example
    website: https://alex.example.com

# Sensitive personal data — stored once, filtered per market.
personal:
  date_of_birth: 1990-01-15       # or: declined
  place_of_birth: Example City
  nationality: [AR, IT]           # ISO 3166-1 alpha-2
  gender: declined
  marital_status: declined
  dependants: declined
  photo: photos/headshot.jpg      # path inside my-cv/
  driving_licence: B
  national_id: declined           # only some markets expect it; never shown unless the market asks

# One entry per target market where work authorisation matters.
work_authorization:
  ca-en: { status: permanent-resident, since: 2025-03, notes: "" }
  ca-fr: { status: permanent-resident, since: 2025-03, notes: "" }
  us-en: { status: requires-sponsorship, notes: "" }

languages:
  - { language: es, native: true }
  - { language: en, cefr: C1, certificate: { name: IELTS Academic, score: "7.5", date: 2025-01 } }
  - { language: fr, cefr: B1, certificate: { name: TEF Canada, score: "CLB 5", date: 2025-06 } }

# Formal credential assessments (DESIGN §8). The official result overrides looked-up equivalences.
credential_assessments:
  - id: eca-wes-2024
    markets: [ca-en, ca-fr]
    organisation: World Education Services (WES)
    type: ECA
    credential: edu-utn-systems
    result: "Bachelor's degree (four years)"
    reference: "0000000"          # fictional
    issued: 2024-11-04
    expires: 2029-11-04
  - id: none-us
    markets: [us-en]
    status: not-started           # the skill leaves a recommendation with the official link

references:
  - name: Jordan Sample
    title: Engineering Manager
    company: Northwind Labs
    relationship: former manager
    contact: jordan.sample@example.com
    consent: true                 # never list a referee without consent
  # Markets that expect "available on request" ignore this list.

preferences:
  roles: [Backend Developer, Platform Engineer]
  seniority: senior
  work_mode: [remote, hybrid]
  salary_expectation: declined

# Generated outputs, so a change can list which ones became stale (DESIGN §13).
outputs:
  - { path: markets/ca-en/cv.md, market: ca-en, generated: 2026-10-07 }
---
```

### Field reference

| Field | Required | Notes |
|---|---|---|
| `schema_version` | yes | Integer. Bumped only when this schema changes incompatibly. |
| `last_updated` | yes | If older than a few months, the skill asks whether there is anything new. |
| `interface_language` | yes | Independent of `target_markets`. |
| `target_markets` | yes | Codes from `markets/`. |
| `name.given`, `name.family` | yes | Written as on official documents. |
| `contact.email`, `contact.city`, `contact.country` | yes | Full street address is never stored. |
| `personal.*` | no | Asked only if a target market uses it. |
| `work_authorization.<market>` | per market | Values: `citizen`, `permanent-resident`, `work-permit`, `open-work-permit`, `requires-sponsorship`, `declined`. |
| `languages[].cefr` | no | `A1`–`C2`. Markets transform it (e.g. "Professional working proficiency", CLB/NCLC). |
| `credential_assessments` | per market | Asked for markets whose file has a `credential_recognition` block. `status: not-started` when the user has none. |
| `references` | no | `consent: true` is mandatory for a referee to appear in any output. |
| `outputs` | managed | Written by the skill, not by the user. |

---

## 2. Body sections

Section headings are fixed in English (`##`). Entries are `###` headings followed by a short key list and bullets. Layouts rename sections per market language.

### `## Summary`

Two to four sentences of free text: role, years of experience, domain, strongest evidence. Markets decide whether it becomes a *Summary*, *Profile*, *Profil* or *Perfil*.

### `## Experience`

```markdown
### Northwind Labs — Senior Backend Developer
- id: exp-northwind
- original_title: Desarrollador Backend Senior
- start: 2021-04
- end: present
- location: Buenos Aires, AR (remote)
- employment: full-time            # full-time | part-time | contract | freelance | internship
- team_size: 6
- stack: [Go, PostgreSQL, Kafka, AWS]

- Cut p95 latency of the payments API from 800 ms to 120 ms by redesigning the cache layer.
- Led the migration of 40 services from EC2 to EKS with zero customer-facing downtime.
- Mentored 3 junior developers; two were promoted within a year.

#### Equivalences
(see the Equivalences format below)
```

- Bullets are *achievements*, ideally quantified (`verb + what + measurable result`). The interview asks for numbers when a bullet has none.
- Keep every bullet the user ever gave; markets and job selection decide how many to show.
- Optional tags at the end of a bullet, e.g. `{leadership, cloud}`, help job selection pick content.

### `## Education`

```markdown
### Universidad Tecnológica Nacional — Ingeniería en Sistemas de Información
- id: edu-utn-systems
- original_degree: Ingeniero en Sistemas de Información
- field: Information systems engineering
- isced_level: 7                   # ISCED 2011 level, used as the bridge between systems
- isced_field: "0613"              # ISCED-F 2013 code
- start: 2009-03
- end: 2015-12
- location: Buenos Aires, AR
- grade: "8.1 / 10"                # original scale; markets decide whether to show or convert it
- thesis: "Event-driven architecture for public transport ticketing"

#### Equivalences
```

### `## Certifications`

```markdown
### AWS Certified Solutions Architect – Associate
- id: cert-aws-saa
- issuer: Amazon Web Services
- issued: 2024-02
- expires: 2027-02
- credential_url: https://www.credly.com/badges/00000000-0000-0000-0000-000000000000
```

### `## Skills`

Grouped lists. Each skill can carry a level (`expert`, `advanced`, `working`) and years.

```markdown
- Languages: Go (expert, 6y), Python (advanced, 8y), TypeScript (working, 3y)
- Data: PostgreSQL (expert), Kafka (advanced), Redis (advanced)
- Cloud & DevOps: AWS (advanced), Kubernetes (advanced), Terraform (working)
- Practices: TDD, code review, incident management
```

### Optional sections

Same entry format (`###` + `id` + key list + bullets): `## Projects`, `## Publications`, `## Volunteering`, `## Awards`, `## Interests`. Markets decide which ones to show.

---

## Equivalences

Each `#### Equivalences` block lives under the role or degree it belongs to. One entry per target market, written by the equivalence resolution step (DESIGN §7). Resolved entries are cached here so they are not looked up again.

```yaml
ca-en:
  chosen: Software Developer
  code: "NOC 2021 21232 — Software developers and programmers"
  rejected:
    - { option: Software Engineer, reason: "'Engineer' is a protected title in Canadian provinces; avoid without a licence" }
    - { option: Backend Programmer, reason: "Rare in current postings" }
  source: https://noc.esdc.gc.ca/
  resolved: 2026-10-07
ca-fr:
  chosen: Développeur de logiciels
  code: "CNP 2021 21232"
  source: https://noc.esdc.gc.ca/
  resolved: 2026-10-07
```

For degrees, an entry that comes from a formal assessment says so and wins over any lookup:

```yaml
ca-en:
  chosen: "Bachelor's degree (four years) in Information Systems Engineering"
  from_assessment: eca-wes-2024
```

Equivalences are guidance, not formal assessments; outputs never present a looked-up equivalence as official.

---

## Complete fictional example

A minimal but complete master profile. All data is invented.

```markdown
---
schema_version: 1
last_updated: 2026-10-07
interface_language: en
target_markets: [ca-en]
name: { given: Alex, family: Example }
contact:
  email: alex.example@example.com
  city: Toronto
  region: ON
  country: CA
work_authorization:
  ca-en: { status: permanent-resident, since: 2025-03 }
languages:
  - { language: es, native: true }
  - { language: en, cefr: C1 }
credential_assessments:
  - { id: eca-wes-2024, markets: [ca-en], organisation: World Education Services (WES), type: ECA, credential: edu-utn-systems, result: "Bachelor's degree (four years)", issued: 2024-11-04, expires: 2029-11-04 }
---

## Summary
Backend developer with 9 years building payment and transport systems in Go and Python. Led cloud migrations of 40+ services with zero downtime.

## Experience

### Northwind Labs — Senior Backend Developer
- id: exp-northwind
- original_title: Desarrollador Backend Senior
- start: 2021-04
- end: present
- location: Buenos Aires, AR (remote)

- Cut p95 latency of the payments API from 800 ms to 120 ms by redesigning the cache layer.

#### Equivalences
    ca-en: { chosen: Software Developer, code: "NOC 2021 21232", source: https://noc.esdc.gc.ca/, resolved: 2026-10-07 }

## Education

### Universidad Tecnológica Nacional — Ingeniería en Sistemas de Información
- id: edu-utn-systems
- original_degree: Ingeniero en Sistemas de Información
- isced_level: 7
- end: 2015-12

#### Equivalences
    ca-en: { chosen: "Bachelor's degree (four years) in Information Systems Engineering", from_assessment: eca-wes-2024 }

## Skills
- Languages: Go (expert), Python (advanced)
```
