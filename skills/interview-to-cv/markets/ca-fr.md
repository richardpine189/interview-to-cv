---
code: ca-fr
name: Québec (français)
family: north-american-resume
template: templates/north-american-resume.md
language: fr-CA
last_verified: 2026-10-07
sources:
  - title: "OQLF, Vitrine linguistique — Conseils pour la rédaction du curriculum vitæ"
    url: https://vitrinelinguistique.oqlf.gouv.qc.ca/22593/la-redaction-et-la-communication/redaction-administrative-et-commerciale/curriculum-vitae/conseils-pour-la-redaction-du-curriculum-vitae
    checked: 2026-10-07
  - title: "OQLF, Vitrine linguistique — Rédaction de la lettre d'accompagnement du curriculum vitæ"
    url: https://vitrinelinguistique.oqlf.gouv.qc.ca/22813/la-redaction-et-la-communication/redaction-administrative-et-commerciale/curriculum-vitae/redaction-de-la-lettre-daccompagnement-du-curriculum-vitae
    checked: 2026-10-07
  - title: "CDPDJ — Formulaires de demande d'emploi et entrevues (Charte, art. 18.1)"
    url: https://www.cdpdj.qc.ca/storage/app/media/publications/formulaire_emploi.pdf
    checked: 2026-10-07
  - title: "Québec.ca (MIFI) — Submitting your comparative evaluation application"
    url: https://www.quebec.ca/en/immigration/work-quebec/recognition-skills-acquired-abroad/getting-comparative-evaluation/submit-application
    checked: 2026-10-07
  - title: "Engineers Canada — 2022 letter on 'ingénieur logiciel' and other IT titles (FR)"
    url: https://engineerscanada.ca/sites/default/files/2022-08/2022-07%20CEO%20Software%20Engineer%20Title%20Letter.FR-signed.pdf
    checked: 2026-10-07
  - title: "Statistics Canada — NOC/CNP 2021 Version 1.0; NOC 2026 planned for December 2026"
    url: https://www.statcan.gc.ca/en/consultation/2024/noc/results-report
    checked: 2026-10-07
---

# Market: Québec, French (`ca-fr`)

French-language applications in Québec. North American structure (`north-american-resume`), Québec French conventions (OQLF). English-language roles in Québec use `ca-en`.

## Include

- Name, city, phone, email, LinkedIn; GitHub or portfolio for technical roles. City only — never a street address.
- *Profil* (summary), *Compétences*, *Expérience professionnelle*, *Formation*, *Certifications*, *Langues*.
- **Langues:** always list French and English. French level matters for most Québec employers; state it plainly even when it is basic.
- **Work authorization:** one line when it helps (`citizen`, `permanent-resident`, `open-work-permit`), e.g. « Résident permanent du Canada ».
- *Engagement social* / *Bénévolat* and *Loisirs* are accepted at the end (OQLF) — include only when relevant or for early career.
- Driving licence class only when the job requires it (OQLF).

## Omit

The Québec Charter of human rights and freedoms (s. 18.1) forbids requiring information tied to discrimination grounds in application forms — the CDPDJ applies this to information that must accompany a CV — and the OQLF lists what has no place in a CV. Never include:

- photo (unless the employer asks)
- age, date of birth, marital status, height, weight, health, religion, political affiliation
- nationality, place of birth, gender, dependants
- social insurance number (NAS) — never
- references, reasons for leaving, salary expectations (OQLF: keep them for the interview)
- full street address

## Transform

| Element | Rule |
|---|---|
| Language | Québec French: *courriel* (not *e-mail*), *cellulaire*, *baccalauréat* for a bachelor's degree, *stage*, *temps plein / temps partiel*. Avoid France-specific terms (*Bac+5*, *alternance*, *CDI*). |
| Bullets | OQLF: action nouns or infinitive verbs (« Concevoir et déployer… », « Migration de 40 services… »). No first person. |
| Dates | Months lowercase, no ordinal: `avril 2021 – aujourd'hui`; education: year only. |
| Section names | Profil · Compétences · Expérience professionnelle · Formation · Certifications · Langues · Projets · Engagement social |
| Language levels | CEFR → *Langue maternelle* / C2 *Bilingue* / C1 *Courant* / B2 *Avancé — usage professionnel* / B1 *Intermédiaire* / A1–A2 *Notions*. If the master profile has an NCLC result from an approved test (TEF Canada, TCF Canada, TEFAQ, TCF Québec), add it in parentheses, e.g. *Courant (NCLC 9)*. |
| Job titles | `equivalences.ca-fr.chosen`. **Never "ingénieur" / "ing."** (ingénieur logiciel, ingénieur DevOps, ingénieur de données…) unless the user is a member of the Ordre des ingénieurs du Québec — reserved title, fined when used on a CV, LinkedIn profile or email signature. Use *Développeur*, *Programmeur*, *Concepteur de logiciels*, *Spécialiste*, *Architecte*. Feminine forms when the user prefers them (*Développeuse*). |
| Degrees | When a MIFI comparative evaluation exists, use its comparison (e.g. « comparable à un baccalauréat québécois ») and name it. Otherwise original name plus a neutral French rendering. Never write *équivalence de diplôme* — the MIFI says its evaluation is not one. |
| Numbers | `1 200` (non-breaking space), `120 ms`, `$` after the amount: `85 000 $`. |
| Company and institution names | Never translated. |

## Constraints

| Constraint | Value |
|---|---|
| Length | 2 pages maximum (OQLF); 1 page for early career. |
| Years shown | Last 10 years of employment, focusing on the last three roles or the most relevant ones (OQLF). |
| Bullets per role | 3–5 for recent roles, 1–2 for older ones. |
| Profil | Recommended; between contact details and skills (OQLF). |
| Cover letter | **Always** (OQLF: a CV sent without a *lettre d'accompagnement* can be rejected outright). One page, three or four paragraphs. |

## Section names (for the template)

```yaml
section_names:
  summary: Profil
  skills: Compétences
  experience: Expérience professionnelle
  education: Formation
  certifications: Certifications
  languages: Langues
  projects: Projets
  volunteer: Engagement social
  cover_letter: Lettre d'accompagnement   # OQLF term; also called lettre de présentation or lettre de motivation
  salutation: Madame, Monsieur,           # or « Madame X, » / « Monsieur Y, » when the name is known
  sign-off: Veuillez agréer, Madame, Monsieur, mes salutations distinguées.
```

## Occupation sources

Query in this order (DESIGN §7):

1. **CNP 2021 version 1.0** (French edition of NOC 2021, https://noc.esdc.gc.ca/?GoCTemplateCulture=fr-CA) — same unit groups as `ca-en`: `21232` Développeurs/développeuses et programmeurs/programmeuses de logiciels, `21234` Développeurs/développeuses et programmeurs/programmeuses Web, `21231` Ingénieurs/ingénieures et concepteurs/conceptrices en logiciel (reserved title — see above), `21223`, `21222`, `21220`, `21211`, `22222`, `20012`. Take the official French titles from the CNP itself.
2. **CNP 2026 version 1.0** is planned for December 2026 — update cached codes after release.
3. **Québec.ca — Explorer un métier ou une profession** and **Qualifications Québec** for Québec usage and regulated professions.
4. **ISCO-08 / CITP-08** as the bridge; current Québec postings (Québec emploi, Jobillico) to validate wording.

## Credential recognition

```yaml
credential_recognition:
  required_for_migration: false   # Québec selects its own immigrants and does not use Express Entry or the federal ECA
  assessment: Évaluation comparative des études effectuées hors du Québec
  organisations:
    - name: Ministère de l'Immigration, de la Francisation et de l'Intégration (MIFI)
      url: https://www.quebec.ca/en/immigration/work-quebec/recognition-skills-acquired-abroad/getting-comparative-evaluation/submit-application
    - name: Qualifications Québec (skills recognition and regulated professions)
      url: https://qualificationsquebec.com/
  official_guidance: https://www.quebec.ca/en/immigration/work-quebec/recognition-skills-acquired-abroad/getting-comparative-evaluation/submit-application
  purpose: >
    Indicative expert opinion that compares studies completed outside Québec with the
    Québec education system. It is not a diploma equivalency, does not bind employers or
    professional orders, and (since 2025-09-04) no longer compares the field of study.
    Employers in Québec recognise it; regulated professions (OIQ for engineers, etc.)
    run their own assessment.
  cost_and_time: >
    $141 CAD (2026, indexed every 1 January); MIFI targets 60 working days with a
    priority-processing letter (employer, professional order, Services Québec), six
    months otherwise. Form A-0361.
  validity: The MIFI does not state an expiry. Re-check at each review.
  when_to_ask: >
    Ask once when ca-fr is a target market and the user studied outside Canada. If yes,
    record the result in credential_assessments and use its wording for degrees. If no,
    recommend it when the user will apply to Québec employers or to a regulated
    profession, and mention that an employer's letter speeds it up. The federal ECA (ca-en)
    and this evaluation are separate processes; a user may need both.
```
