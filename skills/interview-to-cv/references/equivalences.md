# Equivalence resolution

How to map a job title or a degree from the master profile to a target market (DESIGN §7). Run it for every role and degree that has no cached entry for that market, and again when the user asks or a classification version changes.

Equivalences are **guidance, not formal assessments**. Never present a looked-up degree equivalence as official, and never invent one when sources disagree — show the options.

## Before resolving

1. Read the market file's **Occupation sources** and **Transform → Job titles / Degrees** rows; they can forbid wording (e.g. "Engineer" in `ca-en`, "ingénieur" in `ca-fr`).
2. Check `classifications.md` for the version to cite.
3. Look for a cached entry under `#### Equivalences` in the master profile. Reuse it unless the user asks to re-resolve or the cited version is outdated.
4. For degrees, look for a `credential_assessments` entry covering the market. **An official assessment wins**: copy its result verbatim with `from_assessment: <id>` and skip the lookup.

## Track 1 — Job title

1. **Understand the role** from the master profile, not the title alone: tasks, stack, seniority, team size, scope. Titles vary across countries; duties do not.
2. **Find the ISCO-08 unit group** (4 digits) that matches the duties. This is the bridge.
3. **Map to the market's classification** listed in the market file (O\*NET-SOC, NOC, SOC 2020, OSCA, ROME…), using its official correspondence to ISCO-08 when there is one, and its search by title and tasks otherwise.
4. **Read the official example titles** in that unit group and pick 2–3 candidates in the market language.
5. **Validate against current job postings** in the market (official job boards first: Job Bank, Québec emploi, France Travail, USAJOBS / public postings). Prefer the wording that appears most often for the same duties and seniority. LinkedIn is not a data source (no public API; scraping is against its terms).
6. **Apply market constraints** (protected titles, gendered forms, spelling).
7. **Keep the seniority** (Junior / Senior / Lead / Principal) only when the market uses it and the experience supports it.

## Track 2 — Degree and field of study

1. **Identify the level** with ISCED 2011 (`isced_level`) from the official duration and the access requirements of the programme, not from its name. A 5-year *Ingeniería* or *Licenciatura* is not automatically a master's degree.
2. **Identify the field** with ISCED-F 2013 (`isced_field`).
3. **Map the level** to the market's degree vocabulary (Bachelor's / Master's / baccalauréat / licence / master / título de grado…) using credential-evaluator logic: duration, entry requirements, access to further study. Name the evaluator whose public guidance you used (WES, ENIC-NARIC, MIFI…), if any.
4. **Render the field** in the market language without changing what was studied.
5. **Always keep the original name** next to the equivalent in outputs when they differ, e.g. *Bachelor's degree in Information Systems Engineering (Ingeniero en Sistemas de Información, 5 years)*.

## Presenting options to the user

Always offer 2–3 options, recommended first, each with its code and source. Ask the user to pick one; save the choice and the rejected options with their reasons.

```
For your role "Desarrollador Backend Senior" in Canada (English):

1. Senior Software Developer  ← recommended
   NOC 2021 21232 — Software developers and programmers · most common in current Job Bank postings
2. Senior Backend Developer
   Same unit group · common in tech-company postings, less in large employers
3. Senior Software Engineer — not recommended
   "Engineer" is a protected title outside Alberta unless you hold an engineering licence

Which one should I use? (1)
```

## Saving the result

Write the entry under the role's or degree's `#### Equivalences` block, using the format in `master/schema.md`:

```yaml
<market-code>:
  chosen: <title or degree in the market language>
  code: "<classification> <version> <code> — <official title>"
  rejected:
    - { option: <title>, reason: <one line> }
  source: <url>
  resolved: <YYYY-MM-DD>
```

Bump `last_updated` in the master profile and add the affected outputs to the stale list.

## When sources disagree or nothing fits

- Two plausible unit groups → show both, explain the difference in duties, let the user choose.
- No good fit in the national classification → use the closest ISCO-08 group, say so, and pick the posting-validated title.
- A degree whose level is genuinely ambiguous → show the safe rendering (original name + duration + country) and recommend the market's official assessment (`credential_recognition` in the market file).
