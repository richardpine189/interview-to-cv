---
code: us-en
name: United States
family: north-american-resume
template: templates/north-american-resume.md
language: en-US
last_verified: 2026-10-07
sources:
  - title: "EEOC — Prohibited Employment Policies/Practices (pre-employment inquiries)"
    url: https://www.eeoc.gov/prohibited-employment-policiespractices
    checked: 2026-10-07
  - title: "U.S. Department of Education — Recognition of Foreign Qualifications"
    url: https://www.ed.gov/about/initiatives/international-affairs/recognition-of-foreign-qualifications
    checked: 2026-10-07
  - title: "NACES — Current members"
    url: https://www.naces.org/members
    checked: 2026-10-07
  - title: "O*NET 31.0 Database (O*NET-SOC 2019 taxonomy)"
    url: https://www.onetcenter.org/database.html
    checked: 2026-10-07
  - title: "BLS — Standard Occupational Classification (2018 SOC; 2028 revision in progress)"
    url: https://www.bls.gov/soc/
    checked: 2026-10-07
---

# Market: United States (`us-en`)

## Include

- Name, city and state, phone, email, LinkedIn; GitHub or portfolio for technical roles.
- Summary (2–4 lines), skills, experience, education, certifications.
- Languages only when relevant to the job.
- Work authorization **only** when it helps: `citizen`, `permanent-resident` (green card) or a work permit that needs no sponsorship → one short line, e.g. "Authorized to work in the U.S." When the user `requires-sponsorship`, leave it out of the resume and raise it in the strategy notes instead.

## Omit

The EEOC states that race, sex, national origin, age and religion are irrelevant to qualification and that employers should not ask for a photograph before an offer. U.S. resumes therefore never carry:

- photo
- date of birth or age, graduation years older than ~15 years (optional removal, ask the user)
- gender, marital status, dependants
- nationality, place of birth, national ID or Social Security number
- full street address
- references and "References available upon request"
- salary history or expectations

## Transform

| Element | Rule |
|---|---|
| Spelling | American English (`optimize`, `program`, `license`). |
| Dates | `Mon YYYY – Mon YYYY` (e.g. `Apr 2021 – Present`). Education: graduation year only. |
| Section names | Summary · Skills · Experience · Education · Certifications · Languages · Projects |
| Language levels | CEFR → plain words: C2 *Native or bilingual proficiency* / C1 *Full professional proficiency* / B2 *Professional working proficiency* / B1 *Limited working proficiency* / A1–A2 *Elementary proficiency*. Never print CEFR codes. |
| Job titles | `equivalences.us-en.chosen`; never the original title alone. |
| Degrees | U.S. equivalent ("Bachelor of Science in …") only if backed by a NACES/AICE evaluation; otherwise the original name plus a neutral English rendering, e.g. *Ingeniero en Sistemas de Información (5-year degree in Information Systems Engineering, Argentina)*. |
| Grades | Omit unless a converted U.S. GPA from an evaluation exists and is ≥ 3.5. |
| Numbers | `1,200` thousands separator; `$` before amounts; metrics in U.S. units when they matter. |

## Constraints

| Constraint | Value |
|---|---|
| Length | 1 page under ~10 years of experience; 2 pages maximum otherwise. Employer instructions override. |
| Years shown | Last 10–15 years in detail; older roles collapsed into one line or dropped. |
| Bullets per role | 3–6 for recent roles, 1–2 for older ones. |
| Summary | Optional for early career; recommended for experienced and international candidates. |
| Cover letter | One page; often optional — generate when asked or when the posting requests it. |

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
  salutation: Dear
  sign-off: Sincerely,
```

## Occupation sources

Query in this order (DESIGN §7):

1. **O\*NET OnLine** (O\*NET 31.0, O\*NET-SOC 2019 taxonomy) — titles, alternate titles, tasks. Typical IT codes: `15-1252.00` Software Developers, `15-1253.00` Software Quality Assurance Analysts and Testers, `15-1254.00` Web Developers, `15-1244.00` Network and Computer Systems Administrators, `15-1242.00` Database Administrators, `15-1211.00` Computer Systems Analysts.
2. **2018 SOC** (BLS) — the statistical standard behind O\*NET. A 2028 SOC revision is in progress; re-check codes at each review.
3. **ISCO-08** as the bridge from the user's original title.
4. Current U.S. job postings to validate the most used wording.

## Credential recognition

```yaml
credential_recognition:
  required_for_migration: false
  organisations:
    - name: NACES member evaluators (e.g. World Education Services, Educational Credential Evaluators)
      url: https://www.naces.org/members
    - name: AICE member evaluators
      url: https://aice-eval.org/endorsed-members/
  official_guidance: https://www.ed.gov/about/initiatives/international-affairs/recognition-of-foreign-qualifications
  purpose: >
    There is no federal recognition body. The U.S. Department of Education does not
    evaluate foreign degrees; employers, universities, state licensing boards and
    immigration petitions (e.g. H-1B degree equivalency) rely on private evaluation
    reports, usually from NACES or AICE members.
  validity: No fixed expiry; the receiving organisation decides which reports it accepts.
  when_to_ask: >
    Ask once when us-en is a target market. If the user has no evaluation, do not
    block generation; recommend a course-by-course or document-by-document report from
    a NACES/AICE member when the job requires a U.S.-equivalent degree, or when the
    employer will file an H-1B petition. Licensed professions are evaluated by the
    relevant state board instead.
```
