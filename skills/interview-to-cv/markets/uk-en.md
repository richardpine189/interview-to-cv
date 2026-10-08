---
code: uk-en
name: United Kingdom
family: commonwealth-cv
template: templates/commonwealth-cv.md
language: en-GB
last_verified: 2026-10-07
sources:
  - title: "National Careers Service — CV sections"
    url: https://nationalcareers.service.gov.uk/careers-advice/cv-sections
    checked: 2026-10-07
  - title: "GOV.UK — Discrimination: your rights (protected characteristics, Equality Act 2010)"
    url: https://www.gov.uk/discrimination-your-rights
    checked: 2026-10-07
  - title: "GOV.UK — Prove your right to work to an employer"
    url: https://www.gov.uk/prove-right-to-work
    checked: 2026-10-07
  - title: "UK ENIC — Statement of Comparability"
    url: https://www.enic.org.uk/individuals/statement-of-comparability
    checked: 2026-10-07
  - title: "ONS — Standard Occupational Classification (SOC 2020; revision consulted in 2026)"
    url: https://www.ons.gov.uk/methodology/classificationsandstandards/standardoccupationalclassificationsoc
    checked: 2026-10-07
---

# Market: United Kingdom (`uk-en`)

## Include

- Name, town or city, phone, email, LinkedIn (the National Careers Service lists these); GitHub or portfolio for technical roles.
- **Profile** (personal statement, a few short lines under the contact details), key skills, experience, education, certifications.
- **Right to work:** one line when it needs no sponsorship, e.g. "Full right to work in the UK (settled status)" or "British citizen". When the user needs a Skilled Worker visa, leave it out of the CV and cover it in the strategy notes and covering letter.
- Languages when relevant to the job.

## Omit

The National Careers Service advises leaving out age, date of birth, marital status and nationality; age, race (which includes nationality), sex, and marriage or civil partnership are protected characteristics under the Equality Act 2010. Never include:

- photo
- age or date of birth
- marital status, dependants, gender
- nationality, place of birth, National Insurance number
- full street address (town or city is enough)
- referees' names or contact details — at most the line "References available on request"
- salary history or expectations

## Transform

| Element | Rule |
|---|---|
| Spelling | British English: `-ise` (`optimise`, `organise`), `-our`, `-re` (`centre`), `programme` (but `program` for software), `licence` (noun), `analyse`. |
| Dates | `Mon YYYY – Mon YYYY` (e.g. `Apr 2021 – Present`). Education: year only. |
| Section names | Profile · Key Skills · Work Experience · Education · Certifications · Languages · References |
| Language levels | CEFR → *Native* / C2 *Bilingual* / C1 *Fluent* / B2 *Professional working proficiency* / B1 *Intermediate* / A1–A2 *Basic*. Add the test name and score (IELTS, etc.) only when relevant to a visa or the job. |
| Job titles | `equivalences.uk-en.chosen`. "Engineer" is not legally protected in UK job titles (only *Chartered Engineer / CEng* and similar registered titles are), so "Software Engineer" is fine. |
| Degrees | When a UK ENIC Statement of Comparability exists, use its comparison (e.g. "comparable to British Bachelor (Honours) degree standard") and name it. Otherwise original name plus a neutral English rendering. Do not invent a UK degree class (First, 2:1). |
| Numbers | `1,200`; `£` before amounts; metric units. |

## Constraints

| Constraint | Value |
|---|---|
| Length | 2 pages (convention); 1 page for early career. |
| Bullets per role | 2–3 lines or bullets per role is the National Careers Service suggestion; up to 5 for the most recent role. |
| Years shown | Last 10–15 years in detail. |
| Profile | Recommended, a few short lines, no first person. |
| Covering letter | Expected for most applications; one page. |

## Section names (for the template)

```yaml
section_names:
  profile: Profile
  key_skills: Key Skills
  experience: Work Experience
  education: Education
  certifications: Certifications
  languages: Languages
  references: References
  references_line: Available on request
  cover_letter: Covering letter
  salutation: Dear
  sign-off_named: Yours sincerely,
  sign-off_unnamed: Yours faithfully,
```

## Occupation sources

Query in this order (DESIGN §7):

1. **SOC 2020** (ONS) — unit groups and coding index. Typical IT unit groups: `2134` Programmers and software development professionals, `2133` IT business analysts, architects and systems designers, `2135` Cyber security professionals, `2136` IT quality and testing professionals, `2137` IT network professionals, `2139` Information technology professionals n.e.c., `2131` IT project managers, `2132` IT managers. SOC 2010 codes differ (2136 meant programmers in SOC 2010) — always cite the version.
2. **ISCO-08** as the bridge.
3. Current UK postings (Find a job — GOV.UK, employer sites) to validate wording.

The ONS consulted on revising SOC 2020 in 2026; re-check codes at each review. Skilled Worker eligibility uses SOC 2020 codes — mention the code in strategy notes, never on the CV.

## Credential recognition

```yaml
credential_recognition:
  required_for_migration: false   # depends on the visa route; not required for most Skilled Worker applications
  assessment: UK ENIC Statement of Comparability
  organisations:
    - name: UK ENIC (operated by Ecctis on behalf of the UK Government)
      url: https://www.enic.org.uk/individuals/statement-of-comparability
  official_guidance: https://www.enic.org.uk/individuals/statement-of-comparability
  purpose: >
    Certificate comparing an overseas qualification with the UK education system, for
    employment, study or professional registration. Advisory: the employer makes the final
    decision, and it does not comment on grades or subjects. Visa-specific statements
    (e.g. using a degree as English-language evidence) are separate Ecctis services.
  validity: No expiry stated by UK ENIC; statements issued under the former UK NARIC name remain valid.
  when_to_ask: >
    Ask once when uk-en is a target market and the user studied outside the UK. If no,
    recommend it when the user applies to employers that ask for UK-equivalent degrees,
    to regulated professions, or when a visa route needs the degree to be compared. Do
    not present it as mandatory.
```
