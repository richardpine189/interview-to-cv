---
last_verified: 2026-10-07
---

# Classifications

The official classifications the skill uses to resolve equivalences (see `equivalences.md`). Each market file lists which ones to query first; this file records versions, owners and links once, so a version change is updated in one place.

If `last_verified` is older than 6 months, warn the user and offer to re-check versions before resolving new equivalences.

## Bridges (international)

| Classification | Version in use | Owner | Link | Notes |
|---|---|---|---|---|
| **ISCO-08** — International Standard Classification of Occupations | ISCO-08 (2008) | ILO | https://isco.ilo.org/ | Bridge between national occupation classifications. A revision is being prepared by an ILO technical working group; no successor adopted as of the verification date. |
| **ISCED 2011** — International Standard Classification of Education (levels) | ISCED 2011 (ISCED-P / ISCED-A) | UNESCO Institute for Statistics | https://isced.uis.unesco.org/ | Bridge for degree levels (0–8). An amendment is in progress, planned for completion around 2027. |
| **ISCED-F 2013** — Fields of education and training | ISCED-F 2013 | UNESCO Institute for Statistics | https://isced.uis.unesco.org/ | Bridge for fields of study (4-digit codes, e.g. `0613` Software and applications development and analysis). Comprehensive revision planned for around 2027. |
| **ESCO** — European Skills, Competences, Qualifications and Occupations | v1.2.1 (December 2025) | European Commission | https://esco.ec.europa.eu/ | Occupations are mapped to ISCO-08; available in all EU languages. Used for EU markets and as a multilingual label source. |

## National occupation classifications

| Market | Classification | Version in use | Owner | Link | Notes |
|---|---|---|---|---|---|
| `us-en` | **O\*NET-SOC** | O\*NET 31.0, O\*NET-SOC 2019 taxonomy | U.S. Department of Labor / O\*NET Center | https://www.onetcenter.org/database.html | Built on the 2018 SOC. Updated quarterly. |
| `us-en` | **SOC** | 2018 SOC | U.S. Bureau of Labor Statistics | https://www.bls.gov/soc/ | A 2028 SOC revision is in progress. |
| `ca-en`, `ca-fr` | **NOC / CNP** | NOC 2021 Version 1.0 | ESDC and Statistics Canada | https://noc.esdc.gc.ca/ | **NOC 2026 Version 1.0 is planned for December 2026**; update codes with the correspondence table. IRCC may switch later than the release. |
| `uk-en` | **SOC 2020** | SOC 2020 (+ Extended SOC, coding index updates) | Office for National Statistics | https://www.ons.gov.uk/methodology/classificationsandstandards/standardoccupationalclassificationsoc | ONS consulted in 2026 on revising SOC 2020; SOC 2030 in development. |
| `au-en` | **OSCA** | OSCA 2024 Version 1.0 (released 2024-12-06) | Australian Bureau of Statistics | https://www.abs.gov.au/statistics/classifications/osca-occupation-standard-classification-australia/latest-release | Replaces ANZSCO in Australia. **OSCA 2027 Update planned for March 2027.** Some migration and skills-assessment processes may still cite ANZSCO — check the market file. |
| `fr-fr` | **ROME** | ROME 4.0 (since March 2023) | France Travail | https://www.data.gouv.fr/datasets/repertoire-operationnel-des-metiers-et-des-emplois-rome | Updated at least twice a year. Job titles ("appellations") are the most useful field. |
| `fr-fr`, `be-fr` | **ESCO** | v1.2.1 | European Commission | https://esco.ec.europa.eu/ | French labels for EU markets. |

Classifications for `be-fr` and `latam-es` (national adaptations of ISCO-08) are recorded in their market files.

## How to cite a classification in an equivalence

```
code: "<classification> <version> <code> — <official title>"
source: <link to the code's page, or the classification's home page>
resolved: <YYYY-MM-DD>
```

Example: `code: "NOC 2021 21232 — Software developers and programmers"`.

When a classification releases a new version, cached equivalences keep their old code until the user regenerates that market; the quick-update flow then re-resolves them against the new version.
