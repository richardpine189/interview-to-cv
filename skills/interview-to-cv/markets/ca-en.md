---
code: ca-en
name: Canada (English)
family: north-american-resume
template: templates/north-american-resume.md
language: en-CA
last_verified: 2026-10-07
sources:
  - title: "Job Bank (Government of Canada) — How to write a good resume (modified 2024-05-30)"
    url: https://www.jobbank.gc.ca/findajob/resources/write-good-resume
    checked: 2026-10-07
  - title: "IRCC — Education assessed for Express Entry (modified 2026-06-22)"
    url: https://www.canada.ca/en/immigration-refugees-citizenship/services/immigrate-canada/express-entry/documents/education-assessed.html
    checked: 2026-10-07
  - title: "Statistics Canada — NOC 2021 Version 1.0 (page modified 2026-03-20)"
    url: https://www.statcan.gc.ca/en/subjects/standard/noc/2021/indexV1
    checked: 2026-10-07
  - title: "Statistics Canada — Revising NOC 2021 V1.0 to NOC 2026 V1.0 (release planned December 2026)"
    url: https://www.statcan.gc.ca/en/consultation/2024/noc/results-report
    checked: 2026-10-07
  - title: "Engineers Canada — Regulators reiterate licensure requirements for 'software engineer' and other IT titles"
    url: https://engineerscanada.ca/news-and-events/news/engineering-regulators-reiterate-licensure-requirements-for-those-using-software-engineer-and-other-it-titles
    checked: 2026-10-07
  - title: "APEGA — Changes to the Engineering and Geoscience Professions Act regarding the title of Software Engineer (Alberta)"
    url: https://www.apega.ca/news/2023/11/06/notification-of-changes-to-the-engineering-and-geoscience-professions-act-regarding-the-title-of-software-engineer
    checked: 2026-10-07
---

# Market: Canada, English (`ca-en`)

Canada outside Québec, and English-language roles in Québec. French-language applications in Québec use `ca-fr`.

## Include

- Name, city and province, phone, email, LinkedIn; GitHub or portfolio for technical roles. Job Bank asks for contact details at the top of the first page; city and province are enough — never a street address.
- Summary, skills, experience, education, certifications.
- **Languages:** always list English and French levels when either is above A2 — bilingualism is a recognised asset.
- **Work authorization:** one line when it helps — `citizen`, `permanent-resident` or `open-work-permit` → e.g. "Permanent resident of Canada". When the user needs an employer-specific permit (LMIA), leave it out of the resume and cover it in the strategy notes.
- Canadian experience (including volunteering) gets its own entries even when short.

## Omit

Job Bank advises against all of these:

- photo
- Social Insurance Number (SIN) — never
- age or date of birth, height, weight, marital status, religion, political views
- gender, dependants, nationality, place of birth
- references (keep them on a separate sheet, provided on request) and "References available upon request"
- salary history or expectations

## Transform

| Element | Rule |
|---|---|
| Spelling | Canadian English: `-our` (`colour`, `behaviour`), `-re` (`centre`), `-ize` (`organize`), `licence` (noun) / `license` (verb), `program`, `cheque`. |
| Dates | `Mon YYYY – Mon YYYY` (e.g. `Apr 2021 – Present`). Education: graduation year only. |
| Section names | Summary · Skills · Experience · Education · Certifications · Languages · Volunteer Experience · Projects |
| Language levels | CEFR → plain words: C2 *Native or bilingual* / C1 *Fluent* / B2 *Professional working proficiency* / B1 *Intermediate* / A1–A2 *Basic*. If the master profile has a CLB/NCLC result from an approved test, add it in parentheses, e.g. *Fluent (CLB 9)*. |
| Job titles | `equivalences.ca-en.chosen`. **Never use "Engineer" in a title** (Software, Data, DevOps, Cloud, ML… Engineer) unless the user holds a licence from the provincial engineering regulator — regulators in every province except Alberta restrict IT "engineer" titles, including on resumes. Use *Developer*, *Programmer*, *Specialist*, *Architect* instead. Alberta exempts only the exact title "Software Engineer"; ask before using it for Alberta-only applications. Keep the original title in the master profile. |
| Degrees | When an ECA exists, use its result verbatim, followed by "(WES ECA)" or the relevant organisation. Otherwise original name plus a neutral English rendering, as in `us-en`. |
| Grades | Omit, unless an ECA or the posting asks. |
| Numbers | `1,200`; `$` with `CAD` when the currency could be ambiguous. |

## Constraints

| Constraint | Value |
|---|---|
| Length | 2 pages maximum (Job Bank); 1 page for early career. |
| Years shown | Focus on recent experience; cut or minimise roles older than 15 years (Job Bank). |
| Bullets per role | 5–7 maximum per section (Job Bank); 3–5 is the default for recent roles. |
| Summary | Recommended, especially for newcomers: state role, years of experience and work authorization. |
| Cover letter | One page; expected more often than in the U.S. — offer it by default. |

## Section names (for the template)

```yaml
section_names:
  summary: Summary
  skills: Skills
  experience: Experience
  education: Education
  certifications: Certifications
  languages: Languages
  projects: Projects
  volunteer: Volunteer Experience
  salutation: Dear
  sign-off: Sincerely,
```

## Occupation sources

Query in this order (DESIGN §7):

1. **NOC 2021 Version 1.0** (ESDC / Statistics Canada, https://noc.esdc.gc.ca/) — unit group, TEER, example titles. Typical IT unit groups: `21232` Software developers and programmers, `21234` Web developers and programmers, `21231` Software engineers and designers (regulated title — see above), `21223` Database analysts and data administrators, `21222` Information systems specialists, `21220` Cybersecurity specialists, `21211` Data scientists, `22222` Information systems testing technicians, `20012` Computer and information systems managers.
2. **NOC 2026 Version 1.0** is planned for **December 2026**. Once released, check the correspondence table and update cached codes; IRCC may keep using NOC 2021 for a while after the release.
3. **ISCO-08** as the bridge from the user's original title.
4. Job Bank and current Canadian postings to validate the most used wording.

## Credential recognition

```yaml
credential_recognition:
  required_for_migration: true
  assessment: Educational Credential Assessment (ECA)
  organisations:
    - { name: World Education Services (WES), url: https://www.wes.org/ca/ }
    - { name: Comparative Education Service — University of Toronto School of Continuing Studies, url: https://learn.utoronto.ca/comparative-education-service }
    - { name: International Credential Assessment Service of Canada (ICAS), url: https://www.icascanada.ca/ }
    - { name: International Qualifications Assessment Service (IQAS), url: https://www.alberta.ca/iqas-immigration }
    - { name: International Credential Evaluation Service — BCIT (ICES), url: https://www.bcit.ca/ices/ }
    # Architects, physicians and pharmacists use their designated professional body instead (CACB, MCC, PEBC).
  official_guidance: https://www.canada.ca/en/immigration-refugees-citizenship/services/immigrate-canada/express-entry/documents/education-assessed.html
  purpose: >
    Required by IRCC for foreign education under the Federal Skilled Worker Program and
    to earn education points in Express Entry. Employers do not require it, but the
    result is a credible, official equivalence to show on the resume.
  validity: >
    Must be less than 5 years old when the Express Entry profile is created and when
    the application is submitted; an expired ECA leads to refusal.
  when_to_ask: >
    Ask once when ca-en is a target market and the user studied outside Canada. If yes,
    record organisation, result, reference and issue date in credential_assessments,
    and warn 6 months before the 5-year mark. If no and the user plans to immigrate,
    recommend starting an ECA with one of the designated organisations. Regulated
    professions (engineering, nursing, teaching…) also need the provincial regulator's
    own assessment — mention it, do not attempt it.
```
