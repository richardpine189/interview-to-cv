# Interview questions (en)

User-facing wording for the interview. The skill picks the next question from this list, skips every question whose field is already in the master profile, and asks **one question per message**, always with a recommended answer the user can accept as-is.

Format of each question:

- **id** — stable identifier, shared across locales.
- **field** — master-profile path it fills (see `master/schema.md`).
- **ask when** — condition; if false, skip.
- **text** — what the user reads. `{…}` are filled in by the skill.
- **recommended** — how to build the recommended answer.

Message shape:

```
{question text}

Recommended: {recommended answer}
(Reply "ok" to accept, or write your own answer. "skip" to leave it out.)
```

`skip` stores `declined`; the question is not asked again unless the user brings it up.

---

## Start

### start.cv
- field: — (intake)
- ask when: no master profile exists
- text: Do you have a current CV or LinkedIn PDF export? Paste it or attach the file and I'll only ask about what's missing.
- recommended: "Yes — here it is" if the user mentioned one; otherwise "No, start from scratch".

### start.markets
- field: `target_markets`
- ask when: always, unless already set
- text: Which countries are you applying to? Available: {market list with names}.
- recommended: the markets the user mentioned; otherwise the country where they live.

### start.goal
- field: `preferences.roles`, `preferences.seniority`
- ask when: roles not set
- text: What kind of role are you aiming for, and at what level?
- recommended: the most recent title + its seniority.

## Identity and contact

### contact.name
- field: `name.given`, `name.family`
- ask when: missing after intake
- text: What is your full name, as it appears on your official documents?

### contact.location
- field: `contact.city`, `contact.region`, `contact.country`, `contact.willing_to_relocate`
- ask when: missing
- text: Where do you live now (city and country)? Are you willing to relocate for the right job?
- recommended: city from the CV + "yes, willing to relocate" when the target markets differ from the country of residence.

### contact.channels
- field: `contact.email`, `contact.phone`, `contact.links.*`
- ask when: missing
- text: Which email, phone and links (LinkedIn, GitHub, portfolio) should employers see?
- recommended: values from the CV. Warn if the email looks unprofessional.

## Work authorization (one question per target market)

### auth.status
- field: `work_authorization.{market}`
- ask when: a target market has no entry
- text: What is your current status to work in {market name}? (citizen, permanent resident, work permit, open work permit, need sponsorship, prefer not to say)
- recommended: "need sponsorship" when nothing suggests otherwise. Explain in one line how the answer is used in that market (shown only when it helps).

## Credential recognition (only for markets with a `credential_recognition` block)

### cred.has_assessment
- field: `credential_assessments`
- ask when: the user studied outside the target market and has no entry for it
- text: Do you have an official {assessment name} from {organisations}? It's {purpose, one line}.
- recommended: "No" when nothing suggests otherwise.

### cred.details
- field: `credential_assessments[]`
- ask when: the previous answer is yes
- text: What does it say? I need the organisation, the result as written, the reference number and the issue date.

When the answer is no, do not ask more: add the recommendation from `messages.md#cred.recommend` to the session summary.

## Experience (repeat per role, most recent first)

### exp.list
- field: `## Experience`
- ask when: no roles after intake
- text: Let's list your jobs, most recent first. For each: company, your title, city/country, start and end month.

### exp.scope
- field: role `team_size`, `stack`, `employment`
- ask when: missing for a role in the last 10 years
- text: At {company}, what did you work on day to day, with which technologies, and how big was the team?

### exp.achievement
- field: role bullets
- ask when: a recent role has fewer than 3 achievement bullets, or a bullet has no measurable result
- text: What is one result at {company} you're proud of? Something that changed because of your work — faster, cheaper, more users, fewer incidents.
- recommended: rewrite the user's existing duty line as an achievement, with a placeholder for the number: "Reduced {metric} by [?]% by {action}".

### exp.metric
- field: a specific bullet
- ask when: a bullet describes a result without a number
- text: "{bullet}" — can you put a number on it? An estimate is fine if you say it's approximate.
- recommended: "approx." + a conservative range the user can correct. Never invent the number.

### exp.gap
- field: role entry or note
- ask when: a gap longer than 6 months between roles
- text: I see a gap between {end} and {start}. Do you want to show anything for that period (studies, freelance, relocation, family)? It's fine to leave it.
- recommended: "Leave it" unless the user mentioned something.

## Education

### edu.list
- field: `## Education`
- ask when: no degrees after intake
- text: What is your highest completed degree? Institution, exact original name, country, and years.

### edu.duration
- field: degree `start`, `end`, official duration
- ask when: the level is ambiguous for a target market
- text: How many years does {degree} officially take, and what did you need to get in (high-school diploma, a previous degree)?

## Certifications, skills, languages

### cert.list
- field: `## Certifications`
- ask when: none recorded
- text: Any certifications (cloud, security, project management…)? Name, issuer, and date. Include expired ones; I'll decide per market.

### skills.core
- field: `## Skills`
- ask when: fewer than 5 skills recorded
- text: Which technologies and practices would you want an employer to find on your CV? Mark the ones you're strongest at.
- recommended: the skills mentioned across the roles' stacks, grouped.

### lang.levels
- field: `languages`
- ask when: missing, or a target-market language has no level
- text: Which languages do you speak, and at what level? If you have a test result (IELTS, TEF, TCF, DELF…), tell me the score and date.
- recommended: native language + English at the level the CV states.

## Market-specific personal data (only when a target market uses it)

### personal.field
- field: `personal.{field}`
- ask when: a target market's **Include** list needs the field and it is absent
- text: CVs in {market name} sometimes include your {field}. Do you want to add it? You can say no.
- recommended: "No" unless the market file marks it as expected.

## References

### refs.list
- field: `references`
- ask when: a target market lists references and none are recorded
- text: Do you have 1–2 people who agreed to act as references? Name, title, company, how you know them, and contact.
- recommended: "Not now — I'll provide them on request".

## Closing

### close.summary
- field: `## Summary`
- ask when: no summary
- text: Here's a summary based on everything you told me: "{draft}". Want to change anything?
- recommended: the draft itself.

### close.anything_else
- field: —
- ask when: end of the interview
- text: Anything important I didn't ask about — awards, publications, open-source, volunteering?
- recommended: "No, that's all".

## Quick update

### update.what
- field: —
- ask when: the master profile is older than `freshness.ask_after_months` (see SKILL.md) and the user starts a session
- text: Your profile was last updated on {date}. Anything new since then — a job, a certification, a move?
- recommended: "Nothing new".
