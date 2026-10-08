---
code: be-fr
name: Belgique (francophone)
family: french-european-cv
template: templates/french-european-cv.md
language: fr-BE
last_verified: 2026-10-07
sources:
  - title: "EURES — Living and working conditions: Belgium (CV advice; page updated 2026-07-03)"
    url: https://eures.europa.eu/living-and-working/living-and-working-conditions-europe/living-and-working-conditions-belgium_fr
    checked: 2026-10-07
  - title: "Actiris — Rédiger mon CV"
    url: https://www.actiris.brussels/fr/citoyens/mes-outils-pour-postuler/rediger-mon-cv/
    checked: 2026-10-07
  - title: "Unia — protected criteria (anti-discrimination)"
    url: https://www.unia.be/fr
    checked: 2026-10-07
  - title: "Fédération Wallonie-Bruxelles — Equisup: équivalence and reconnaissance professionnelle of foreign higher-education diplomas"
    url: https://equisup.cfwb.be/
    checked: 2026-10-07
  - title: "Equisup — Guide 2026: introduire une demande (équivalence de niveau / à un grade spécifique)"
    url: https://equisup.cfwb.be/fileadmin/sites/equisup/uploads/Guides/Fr_guide_CAMA_RA_2026_introduire_une_demande.pdf
    checked: 2026-10-07
  - title: "Actiris — Panorama des métiers"
    url: https://panorama.actiris.brussels/fr/accueil/
    checked: 2026-10-07
---

# Market: Belgium, French-speaking (`be-fr`)

Wallonia and French-language applications in Brussels. Flemish employers expect Dutch; this market does not cover them.

## Include

- Name, city, phone in international format (`+32 …`), email, LinkedIn; GitHub or portfolio for technical roles. EURES lists the address among the header items; city and postcode are enough.
- **Titre du CV / objectif professionnel** — Actiris lists a career-objective heading.
- Expérience professionnelle, Formation, Compétences, Certifications.
- **Langues — always, in their own section, with CEFR levels.** EURES stresses that language skills matter a great deal in Belgium; state French, Dutch, English (and German if any) explicitly, even at basic level.
- **Right to work:** one line when the user is not an EU/EEA/Swiss citizen and holds a permit that allows work, e.g. « Titulaire d'un permis unique autorisant le travail en Belgique ».

## Omit

EURES advises avoiding age, nationality, family situation and sex to limit the risk of discrimination; Unia lists nationality, origin, age, health, conviction and sexual orientation among protected criteria. Never include:

- **photo** — only if the job requires it or the employer asks (EURES, Actiris)
- age or date of birth
- marital status, children
- nationality, place of birth, gender
- national register number
- references (on request)
- salary expectations

## Transform

| Element | Rule |
|---|---|
| Language | Belgian French usage: *bachelier* (bachelor's), *master*, *GSM* (mobile), *septante / nonante* only if the user writes that way — digits are safer. Avoid France-only shorthand (*Bac+5*). |
| Bullets | Action nouns or verbs, no first person. |
| Dates | `avril 2021 – aujourd'hui`; education: year only. |
| Section names | Objectif professionnel · Expérience professionnelle · Formation · Compétences · Langues · Certifications · Informations complémentaires |
| Language levels | CEFR code with words, as in `fr-fr`: *Langue maternelle* / *C2 — bilingue* / *C1 — courant* / *B2 — avancé* / *B1 — intermédiaire* / *A2 — notions*. |
| Job titles | `equivalences.be-fr.chosen`. *Ingénieur civil* and *ingénieur industriel* are protected academic titles (law of 11 September 1933): use them only for holders of those Belgian degrees or of an equivalence to them. Prefer *Développeur*, *Analyste-programmeur*, *Architecte logiciel*. English titles (Software Engineer) are common in Brussels IT postings; ask the user which language the posting uses. |
| Degrees | When an FWB equivalence exists, use its wording (level or specific degree) and name it. Otherwise original name + duration + country, mapped to *bachelier* (3 years) or *master* (1–2 years after a bachelier) only when duration and access requirements support it. |
| Numbers | `1 200`, `45 000 €`. |
| Company and institution names | Never translated. |

## Constraints

| Constraint | Value |
|---|---|
| Length | 2 A4 pages maximum (Actiris); 1 page for early career. |
| Bullets per role | 3–5 for recent roles. |
| Years shown | Last 10–15 years in detail. |
| Lettre de motivation | Expected; one page; tailored to the company and post (EURES). For *candidatures spontanées*, state the professional goal and why this company. |

## Section names (for the template)

```yaml
section_names:
  profile: Objectif professionnel
  experience: Expérience professionnelle
  education: Formation
  skills: Compétences
  languages: Langues
  certifications: Certifications
  interests: Informations complémentaires
  cover_letter: Lettre de motivation
  salutation: Madame, Monsieur,
  closing: Je me tiens à votre disposition pour un entretien.
  formule de politesse: Je vous prie d'agréer, Madame, Monsieur, l'expression de mes salutations distinguées.
```

## Occupation sources

Query in this order (DESIGN §7):

1. **ESCO v1.2.1** — French labels mapped to ISCO-08; the common EU reference.
2. **Actiris — Panorama des métiers** (Brussels; built on a VDAB referential) and **Le Forem** job descriptions (Wallonia) for Belgian wording.
3. **ROME 4.0** as a French-language aid for job titles (e.g. `M1805`), not as a Belgian standard.
4. **ISCO-08** as the bridge.
5. Current postings (Actiris, Le Forem) to validate wording and the language of the posting.

No single national occupation classification for job titles was identified for French-speaking Belgium; cite ESCO codes.

## Credential recognition

```yaml
credential_recognition:
  required_for_migration: false
  assessment: Équivalence de diplôme étranger d'enseignement supérieur (Fédération Wallonie-Bruxelles)
  organisations:
    - name: Fédération Wallonie-Bruxelles — Direction de la reconnaissance des diplômes étrangers (Equisup)
      url: https://equisup.cfwb.be/
    - name: NARIC-Vlaanderen (only for jobs in Flanders)
      url: https://www.naric.be/
  official_guidance: https://equisup.cfwb.be/
  purpose: >
    Two kinds of decision: equivalence of study level, or equivalence to a specific
    Belgian degree. Usually not needed for private-sector jobs; very likely needed for
    public-sector or publicly subsidised employers, for the salary scale tied to the degree
    level, and for regulated professions (which also go through professional recognition).
    The online application is filed on Equisup. The procedure depends on where the user
    will work (FWB vs Flanders), not where they live.
  validity: No expiry stated on the pages verified.
  cost_and_time: Check Equisup at request time; fees and delays were not published on the pages verified.
  when_to_ask: >
    Ask once when be-fr is a target market and the user studied outside Belgium. If no,
    recommend it when the user targets public or subsidised employers, regulated
    professions, or a salary scale based on degree level; otherwise mention it as optional.
```
