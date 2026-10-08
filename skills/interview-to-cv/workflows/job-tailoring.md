# Workflow: job tailoring and match score

The user pastes a job posting (text, link content or file). The skill analyses it once and uses the analysis for the match score, the tailored CV and the cover letter (DESIGN §10).

**Never invent experience.** Requirements the master profile does not support are reported as gaps — never written into the CV or the letter. Show `messages.md#match.never_invent` the first time.

## 1. Set up the application

1. Ask for the posting if it was not given. Extract: company, job title, location, market (country + language), seniority, contract type, reference number, and contact name if any.
2. Pick the market file from the location and the posting's language (e.g. a French posting in Montréal → `ca-fr`; an English posting in Toronto → `ca-en`). If ambiguous, ask with a recommended answer.
3. Create `my-cv/applications/<yyyy-mm>-<company>-<role>/` (kebab-case) and save the posting as `job.md` with the extracted fields as front matter.

## 2. Analyse the posting

Split requirements into:

- **Must-haves** — "required", "must", "X+ years", listed under requirements/qualifications.
- **Nice-to-haves** — "preferred", "a plus", "bonus", "ideally".
- **Keywords** — technologies, methods, domains and certifications, in the posting's exact wording.
- **Seniority signal** — years, scope (team lead, architecture, mentoring), title level.
- **Location / visa** — on-site, hybrid or remote; country restrictions; sponsorship offered or excluded.

For each requirement, find evidence in the master profile (role id + bullet, certification, degree, skill). Mark it `met`, `partial` (related evidence: adjacent technology, fewer years) or `gap`.

## 3. Match score

A breakdown, not a single magic number:

```
Match — Senior Backend Developer @ Northwind Labs (ca-en)

Must-haves     5 / 6 met · 1 partial
  ✅ 5+ years backend (9 years — exp-northwind, exp-contoso)
  ✅ Go in production (exp-northwind)
  ◐ Kubernetes — you used EKS for the migration; no admin experience listed
  …
Nice-to-haves  2 / 4
Keywords       14 / 18 present in your profile (4 missing: gRPC, Terraform, SOC 2, on-call)
Seniority      ✅ aligned (Senior; you led a 40-service migration and mentored 3)
Location/visa  ✅ Toronto hybrid · you are a permanent resident

Overall: strong fit (must-haves nearly complete)
```

Overall label from must-haves first: all met → *strong fit*; one partial or gap → *good fit*; two or more gaps → *stretch*; a hard blocker (visa excluded, required licence) → *blocked* — say which.

## 4. Gaps and strategy

For each gap or partial:

- Ask whether the user has evidence not yet in the profile ("Have you used gRPC anywhere, even in a side project?"). Save new facts to the master profile.
- If not, suggest how to address it honestly: mention adjacent experience in the letter, a short course or certification, or simply apply anyway when must-haves are mostly met.

Add an **application strategy** (3–5 lines): whether to apply, what to emphasise, what to prepare for the interview, and visa notes when relevant (from the market file — never on the CV).

## 5. Tailored CV

Generate the market CV (`SKILL.md` step 4) with job selection:

- **Reorder** skills, roles' bullets and certifications so evidence for must-haves comes first.
- **Select** the bullets that match the posting; drop unrelated ones before cutting relevant ones.
- **Mirror wording** from the posting when the master profile supports it (posting says "CI/CD pipelines", profile says "build pipelines" → use the posting's term).
- **Summary** rewritten for this job: role, years, top 2 matching achievements.
- Run the ATS check with keyword check (#10) on.

Save as `applications/<…>/cv.md`.

## 6. Cover letter

Offer it (or generate it if the market file says it is expected). Follow `workflows/cover-letter.md`, using this analysis for the evidence slots. Save as `applications/<…>/cover-letter.md`.

## 7. Wrap-up

List the files created, the match summary, the open gaps and the checklist from `messages.md#letter.checklist` when a letter was written.
