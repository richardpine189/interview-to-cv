---
schema_version: 1
last_updated: 2026-10-07
interface_language: es
target_markets: [ca-en, ca-fr, latam-es]

name:
  given: Alex
  family: Example
pronouns: they/them

contact:
  email: alex.example@example.com
  phone: "+1 555 0100"
  city: Toronto
  region: ON
  country: CA
  willing_to_relocate: true
  links:
    linkedin: https://www.linkedin.com/in/alex-example
    github: https://github.com/alex-example

personal:
  date_of_birth: declined
  nationality: declined
  marital_status: declined
  photo: declined

work_authorization:
  ca-en: { status: permanent-resident, since: 2025-03 }
  ca-fr: { status: permanent-resident, since: 2025-03 }
  latam-es: { status: citizen, notes: "Argentina" }

languages:
  - { language: es, native: true }
  - { language: en, cefr: C1, certificate: { name: IELTS General Training, score: "7.5", date: 2024-09 } }
  - { language: fr, cefr: B1 }

credential_assessments:
  - id: eca-wes-2024
    markets: [ca-en, ca-fr]
    organisation: World Education Services (WES)
    type: ECA
    credential: edu-utn-systems
    result: "Bachelor's degree (four years)"
    reference: "0000000"
    issued: 2024-11-04
    expires: 2029-11-04

references: []

preferences:
  roles: [Backend Developer, Platform Developer]
  seniority: senior
  work_mode: [remote, hybrid]

outputs:
  - { path: markets/ca-en/cv.md, market: ca-en, generated: 2026-10-07 }
---

<!-- Fictional example. Every person, company and number below is invented. -->

## Summary

Backend developer with 9 years building payment and ticketing systems in Go and Python. Led the migration of 40 services to Kubernetes with zero customer-facing downtime and cut payment API latency by 85%.

## Experience

### Northwind Labs — Senior Backend Developer
- id: exp-northwind
- original_title: Desarrollador Backend Senior
- start: 2021-04
- end: present
- location: Buenos Aires, AR (remote)
- employment: full-time
- team_size: 6
- stack: [Go, PostgreSQL, Kafka, AWS, Kubernetes]

- Cut p95 latency of the payments API from 800 ms to 120 ms by redesigning the cache layer. {performance}
- Led the migration of 40 services from EC2 to EKS with zero customer-facing downtime. {cloud, leadership}
- Mentored 3 junior developers; two were promoted within a year. {leadership}
- Introduced contract tests between 12 services, reducing integration incidents by about 60% (approx.). {quality}

#### Equivalences
```yaml
ca-en:
  chosen: Senior Software Developer
  code: "NOC 2021 21232 — Software developers and programmers"
  rejected:
    - { option: Senior Software Engineer, reason: "'Engineer' is a protected title outside Alberta without a licence" }
  source: https://noc.esdc.gc.ca/
  resolved: 2026-10-07
ca-fr:
  chosen: "Spécialiste en développement de logiciels, niveau avancé"  # epicene form for they/them
  code: "CNP 2021 21232"
  source: https://noc.esdc.gc.ca/
  resolved: 2026-10-07
latam-es:
  chosen: Desarrollador/a Backend Senior
  code: "CIUO-08 2512 — Desarrolladores de software"
  source: https://isco.ilo.org/
  resolved: 2026-10-07
```

### Contoso Transit — Backend Developer
- id: exp-contoso
- original_title: Desarrollador Backend
- start: 2017-03
- end: 2021-03
- location: Buenos Aires, AR
- employment: full-time
- stack: [Python, Django, PostgreSQL, Redis]

- Built the fare-calculation service used by 1.2 million daily trips.
- Reduced nightly batch time from 4 hours to 35 minutes by moving to incremental processing.
- Maintained the public trip-planner API (99.95% uptime over two years).

#### Equivalences
```yaml
ca-en: { chosen: Software Developer, code: "NOC 2021 21232", source: https://noc.esdc.gc.ca/, resolved: 2026-10-07 }
ca-fr: { chosen: Spécialiste en développement de logiciels, code: "CNP 2021 21232", source: https://noc.esdc.gc.ca/, resolved: 2026-10-07 }
latam-es: { chosen: Desarrollador/a Backend, code: "CIUO-08 2512", source: https://isco.ilo.org/, resolved: 2026-10-07 }
```

## Education

### Universidad Tecnológica Nacional — Ingeniería en Sistemas de Información
- id: edu-utn-systems
- original_degree: Ingeniero en Sistemas de Información
- field: Information systems engineering
- isced_level: 7
- isced_field: "0613"
- start: 2009-03
- end: 2015-12
- location: Buenos Aires, AR

#### Equivalences
```yaml
ca-en: { chosen: "Bachelor's degree (four years) in Information Systems Engineering", from_assessment: eca-wes-2024 }
ca-fr: { chosen: "Baccalauréat (quatre ans) en ingénierie des systèmes d'information", from_assessment: eca-wes-2024 }
latam-es: { chosen: "Ingeniería en Sistemas de Información", resolved: 2026-10-07 }
```

## Certifications

### AWS Certified Solutions Architect – Associate
- id: cert-aws-saa
- issuer: Amazon Web Services
- issued: 2024-02
- expires: 2027-02

## Skills

- Languages: Go (expert, 6y), Python (advanced, 8y), SQL (advanced)
- Data: PostgreSQL (expert), Kafka (advanced), Redis (advanced)
- Cloud & DevOps: AWS (advanced), Kubernetes (advanced), Terraform (working), GitHub Actions
- Practices: contract testing, code review, incident management, mentoring
