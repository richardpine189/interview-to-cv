---
code: au-en
name: Australia
family: commonwealth-cv
template: templates/commonwealth-cv.md
language: en-AU
last_verified: 2026-10-07
sources:
  - title: "Australian Human Rights Commission — IncludeAbility: Writing a resumé and cover letter"
    url: https://humanrights.gov.au/resource-hub/resources-for-organisations-businesses/disability-resources-employers/includeability-equality-work/career-and-job-seeking-resources/writing-a-resume-and-cover-letter
    checked: 2026-10-07
  - title: "Workforce Australia — resume template (referees guidance)"
    url: https://www.workforceaustralia.gov.au/content/online-learning/course/use-resume-templates-to-not-start-from-scratch/assets/job%20jumpstart%20resume%20clean%20temp.pdf
    checked: 2026-10-07
  - title: "Your Career — Australian Jobs 2025 (resume length 1–2 pages)"
    url: https://content.yourcareer.gov.au/sites/default/files/2025-06/Australian%20Jobs%202025.pdf
    checked: 2026-10-07
  - title: "ACS — Migration Skills Assessment, IT occupations and ANZSCO codes"
    url: https://www.acs.org.au/msa/information-for-applicants/occupations-anzsco-codes/information-technology.html
    checked: 2026-10-07
  - title: "ACS — Migration Skills Assessment service agreement (outcomes valid 2 years)"
    url: https://www.acs.org.au/msa/infohub/service-agreement.html
    checked: 2026-10-07
  - title: "ABS — OSCA 2024 Version 1.0 (OSCA 2027 Update planned March 2027)"
    url: https://www.abs.gov.au/statistics/classifications/osca-occupation-standard-classification-australia/latest-release
    checked: 2026-10-07
---

# Market: Australia (`au-en`)

## Include

- Name, suburb/city and state, phone, email, LinkedIn; GitHub or portfolio for technical roles.
- Career profile, key skills, experience, education, certifications.
- **Referees:** Australian government guidance (AHRC, Workforce Australia) expects referee details at the end of the résumé — usually two — or "Available on request". List them only when the master profile has referees with `consent: true`; for each: name, current title, organisation, working relationship, phone/email.
- **Work rights:** one line when they help — `citizen`, `permanent-resident`, or a visa with full work rights, e.g. "Australian permanent resident" or "Full work rights (subclass 485 visa until 2028-03)". When the user needs employer sponsorship, leave it out and cover it in strategy notes.
- **Selection criteria:** public-sector and many large-employer postings list key selection criteria; the cover letter (or a separate statement) addresses each one.

## Omit

- photo (not expected; include only if an employer asks)
- age or date of birth
- gender, marital status, dependants
- nationality, place of birth, Tax File Number
- full street address
- salary history or expectations

## Transform

| Element | Rule |
|---|---|
| Spelling | Australian English: `-ise` (`organise`, `optimise`), `-our`, `-re` (`centre`), `program` (software and general), `licence` (noun). |
| Dates | `Mon YYYY – Mon YYYY` (e.g. `Apr 2021 – Present`). Education: year only. |
| Section names | Career Profile · Key Skills · Employment History · Education · Certifications · Languages · Referees |
| Language levels | CEFR → *Native* / C2 *Bilingual* / C1 *Fluent* / B2 *Professional working proficiency* / B1 *Intermediate* / A1–A2 *Basic*. Add an IELTS/PTE score only when relevant to a visa or the posting. |
| Job titles | `equivalences.au-en.chosen`. "Software Engineer" is a standard Australian title (ANZSCO 261313, used by the ACS). Only registered-engineer titles (e.g. *RPEQ* in Queensland) need registration; never claim them without it. |
| Degrees | When an ACS assessment exists, use its wording (e.g. "assessed as comparable to an AQF Bachelor Degree with a major in computing") and name the ACS. Otherwise original name plus a neutral English rendering. |
| Numbers | `1,200`; `$` with `AUD` when ambiguous; metric units. |

## Constraints

| Constraint | Value |
|---|---|
| Length | 2 pages for most candidates (Your Career suggests 1–2); up to 3 for senior candidates with long relevant histories. |
| Bullets per role | 3–6 for recent roles. |
| Years shown | Last 10–15 years in detail. |
| Cover letter | Expected; one page. Address selection criteria when listed. |

## Section names (for the template)

```yaml
section_names:
  profile: Career Profile
  key_skills: Key Skills
  experience: Employment History
  education: Education
  certifications: Certifications
  languages: Languages
  references: Referees
  references_line: Available on request
  cover_letter: Cover letter
  salutation: Dear
  sign-off_named: Yours sincerely,
  sign-off_unnamed: Kind regards,
```

## Occupation sources

Query in this order (DESIGN §7):

1. **OSCA 2024 Version 1.0** (ABS) — the statistical standard for job titles and tasks in Australia. The **OSCA 2027 Update** is planned for March 2027.
2. **ANZSCO** — still used by the ACS and by migration occupation lists. Typical ICT codes (ACS): `261313` Software Engineer, `261312` Developer Programmer, `261311` Analyst Programmer, `261316` DevOps Engineer, `261314` Software Tester, `261212` Web Developer, `261111` ICT Business Analyst, `261112` Systems Analyst, `262111` Database Administrator, `262112` ICT Security Specialist, `263111` Computer Network and Systems Engineer, `135112` ICT Project Manager. Record both the OSCA and the ANZSCO code when the user plans to migrate.
3. **ISCO-08** as the bridge.
4. Current Australian postings (Workforce Australia, APSjobs for public sector) to validate wording.

## Credential recognition

```yaml
credential_recognition:
  required_for_migration: true    # for skilled visas in ICT occupations
  assessment: ACS Migration Skills Assessment
  organisations:
    - name: Australian Computer Society (ACS) — assessing authority for ICT occupations
      url: https://www.acs.org.au/msa.html
  official_guidance: https://www.acs.org.au/msa/information-for-applicants/occupations-anzsco-codes/information-technology.html
  purpose: >
    Required for most skilled visas in ICT occupations. Assesses whether qualifications
    and work experience are at professional ICT level and closely related to the nominated
    ANZSCO occupation (up to three); qualifications are rated as ICT Major, Minor or
    insufficient. Occupation lists change — confirm on the Department of Home Affairs list.
  validity: Suitable outcomes are valid for 2 years.
  when_to_ask: >
    Ask once when au-en is a target market and the user plans to migrate or needs a visa.
    If yes, record the nominated ANZSCO code, outcome and date in credential_assessments
    and warn 3 months before the 2-year mark. If no, recommend the ACS assessment before
    lodging an expression of interest. Users already holding full work rights do not need it
    for employers.
```
