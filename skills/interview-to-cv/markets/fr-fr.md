---
code: fr-fr
name: France
family: french-european-cv
template: templates/french-european-cv.md
language: fr-FR
last_verified: 2026-10-07
sources:
  - title: "Légifrance — Code du travail, art. L1221-6 (information requested from candidates)"
    url: https://www.legifrance.gouv.fr/codes/article_lc/LEGIARTI000006900845
    checked: 2026-10-07
  - title: "Légifrance — Code du travail, Recrutement (art. L1221-6 to L1221-9)"
    url: https://www.legifrance.gouv.fr/codes/section_lc/LEGITEXT000006072050/LEGISCTA000006189415/
    checked: 2026-10-07
  - title: "EURES — Living and working conditions: France (CV max. 2 pages; letter max. 1 page; page updated 2026-07-03)"
    url: https://eures.europa.eu/living-and-working/living-and-working-conditions/living-and-working-conditions-france_fr
    checked: 2026-10-07
  - title: "France Éducation international — ENIC-NARIC France: comment demander une attestation"
    url: https://www.france-education-international.fr/article/comment-demander-une-attestation
    checked: 2026-10-07
  - title: "Onisep — Le titre d'ingénieur"
    url: https://www.onisep.fr/orientation/l-enseignement-superieur/quelle-reconnaissance-pour-les-diplomes-du-superieur/le-titre-d-ingenieur
    checked: 2026-10-07
  - title: "data.gouv.fr — ROME 4.0 (France Travail)"
    url: https://www.data.gouv.fr/datasets/repertoire-operationnel-des-metiers-et-des-emplois-rome
    checked: 2026-10-07
---

# Market: France (`fr-fr`)

## Include

- Name, city, phone in international format, email, LinkedIn; GitHub or portfolio for technical roles.
- **Titre du CV** (target job headline) — EURES recommends it.
- Expérience professionnelle, Formation, Compétences, **Langues** (always), Certifications; short *Centres d'intérêt* optional (EURES suggests mentioning previous stays in France there).
- **Right to work:** one line when it helps and the user is not an EU/EEA/Swiss citizen, e.g. « Titulaire d'un titre de séjour autorisant à travailler ». EU/EEA citizens do not need to state it.
- Salary expectations are **not** on the CV; they go in the letter only when the posting asks for them.

## Omit

The Code du travail (art. L1221-6) limits what can be asked of candidates to information with a direct and necessary link to the job, and art. L1132-1 forbids excluding a candidate on grounds including age, family situation, origin, nationality and physical appearance. EURES lists age, family situation and nationality as optional on a French CV. This skill omits them by default:

- age or date of birth
- marital status, children
- nationality, place of birth, gender
- social security number
- full street address (city is enough)
- **photo — off by default.** It is common in France but optional. Offer it only if the user asks or the posting requires it, with a note that physical appearance is a discrimination ground and anonymous review is encouraged.
- references (provide on request; reference letters, if any, are translated into French)

## Transform

| Element | Rule |
|---|---|
| Language | Metropolitan French: *mail / e-mail* or *courriel*, *portable*, *CDI / CDD* (contract types) when relevant, *alternance*, *stage*. |
| Bullets | Action nouns or verbs (infinitive or *passé composé*), no first person. |
| Dates | `avr. 2021 – aujourd'hui` or `depuis avril 2021`; education: year only. |
| Section names | Profil · Expérience professionnelle · Formation · Compétences · Langues · Certifications · Centres d'intérêt |
| Language levels | Keep the CEFR code with words: *Langue maternelle* / *C2 — bilingue* / *C1 — courant* / *B2 — avancé* / *B1 — intermédiaire* / *A2 — notions*. Add a certificate (TOEIC, IELTS, DELF/DALF, TCF) with its score when held. |
| Job titles | `equivalences.fr-fr.chosen`. *Ingénieur* is not a protected job title in France and is widely used in IT (*Ingénieur logiciel*, *Ingénieur DevOps*). Only *ingénieur diplômé* (degree from a CTI-accredited school) is protected — never claim it without that degree. |
| Degrees | When an ENIC-NARIC France attestation exists, use its level (e.g. « niveau 7 du cadre national des certifications professionnelles — équivalent Bac+5 ») and name it. Otherwise original name + duration + country. French readers use *Bac+N*: Bac+3 ≈ licence / bachelor (niveau 6), Bac+5 ≈ master (niveau 7); only state a *Bac+N* level when the duration and access requirements support it. |
| Numbers | `1 200` (non-breaking space), `120 ms`, `45 k€` or `45 000 €`. |
| Company and institution names | Never translated. |

## Constraints

| Constraint | Value |
|---|---|
| Length | 1 page for early career and up to ~8 years; 2 pages maximum (EURES). |
| Bullets per role | 3–5 for recent roles, 1–2 for older ones. |
| Years shown | Last 10–15 years in detail. |
| Lettre de motivation | One page maximum (EURES); expected for most applications and for *candidatures spontanées*. |

## Section names (for the template)

```yaml
section_names:
  profile: Profil
  experience: Expérience professionnelle
  education: Formation
  skills: Compétences
  languages: Langues
  certifications: Certifications
  interests: Centres d'intérêt
  cover_letter: Lettre de motivation
  salutation: Madame, Monsieur,           # « Madame X, » when the name is known
  closing: Je serais heureux·se de vous exposer plus en détail ma motivation lors d'un entretien.
  formule de politesse: Je vous prie d'agréer, Madame, Monsieur, l'expression de mes salutations distinguées.
```

## Occupation sources

Query in this order (DESIGN §7):

1. **ROME 4.0** (France Travail) — job sheets (*fiches métiers*) and their *appellations*; e.g. `M1805` Études et développement informatique. Use the appellations to pick the title.
2. **ESCO v1.2.1** — French labels mapped to ISCO-08.
3. **ISCO-08 (CITP-08)** as the bridge.
4. Current postings (France Travail, APEC for *cadres*, Welcome to the Jungle) to validate wording.

## Credential recognition

```yaml
credential_recognition:
  required_for_migration: false
  assessment: Attestation de comparabilité (ENIC-NARIC France)
  organisations:
    - name: Centre ENIC-NARIC France — France Éducation international
      url: https://www.france-education-international.fr/article/comment-demander-une-attestation
  official_guidance: https://www.france-education-international.fr/article/comment-demander-une-attestation
  purpose: >
    Compares a foreign diploma with the French system (level in the national framework).
    Not mandatory and not legally binding: employers, schools and competition organisers
    decide. Since 2026-01-01 it is no longer accepted for naturalisation applications.
  cost_and_time: "120 € (20 € at filing + 100 € before review); one diploma per file; average 3–4 months."
  validity: No expiry stated.
  regulated_professions: Regulated professions use their own procedure (competent authority per profession), not the attestation.
  when_to_ask: >
    Ask once when fr-fr is a target market and the user studied outside France. If no,
    recommend it when the posting asks for a French-equivalent degree (Bac+5, niveau 7),
    for public competitions, or when the degree name will not be understood by French
    recruiters. Mention the processing time so the user can start early.
```
