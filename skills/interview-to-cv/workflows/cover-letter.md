# Workflow: cover letters

Letters that read as if they were written for this company, not for any company (DESIGN §9). The layout and the market's variant name come from the family template (`templates/<family>.md`, "Cover letter skeleton") and the market file's `section_names`.

## 1. Type

Ask which type, with a recommended answer from context (a pasted posting → *job posting*):

| Type | Needs |
|---|---|
| Job posting | Posting analysis from `workflows/job-tailoring.md` |
| Unsolicited (*candidature spontanée*, *postulación espontánea*) | Company, target team or role type |
| Referral | Referrer's name and relationship; confirm the referrer agreed to be named |
| Career change | Previous field, what transfers, why the change |
| Relocation | Target country/city, why there, work authorization status |

## 2. Fill the evidence slots

Each `<<…>>` slot in the template needs a specific fact. Get it in this order:

1. From the job analysis and the master profile (achievements mapped to requirements).
2. From the user — one question per slot, with a recommended answer when possible. For "why this company", ask what drew them; offer to look up recent public facts about the company (product launches, engineering blog, funding, values) and let the user pick one they genuinely care about.
3. If the user has nothing: leave the slot visible as `<<…>>` and show `messages.md#letter.empty_slot`. **Never fill a slot with a generic sentence.**

## 3. Write

- Market language, register and formulas from the market file (salutation, closing, sign-off).
- One page; three to four paragraphs (five at most in the Commonwealth family).
- No claims that are not in the master profile or stated by the user in this session.
- No salary, personal data or visa details beyond what the market file allows.
- Do not repeat the CV: pick two achievements and give them context.

## 4. Check (every letter)

Run all four before showing the letter:

1. **Generic-language check** — match every sentence against `locales/<interface lang>/generic-phrases.md` (and the output language's list when it exists). Show matches with `messages.md#letter.generic_found` and propose a specific rewrite for each.
2. **"Could this be sent to any company?"** — for each paragraph, test whether replacing the company name with a competitor's leaves it true. If yes, flag it with `messages.md#letter.any_company`.
3. **Slot check** — list any `<<…>>` still open.
4. **Fact check** — every number, name and date appears in the master profile, the posting or the user's answers.

## 5. Deliver

Show, in this order:

1. `messages.md#letter.warning` — **always, before the letter**.
2. The letter.
3. The results of the checks.
4. `messages.md#letter.checklist`.

Save as `my-cv/applications/<…>/cover-letter.md` (job posting) or `my-cv/letters/<yyyy-mm>-<company>.md` (other types).
