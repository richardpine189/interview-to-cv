# Workflow: quick update

Short changes to an existing master profile — "I got the AWS certification", "I changed jobs in August", "I moved to Lyon" — without re-running the interview (DESIGN §13).

## 1. Identify the change

Classify the user's message:

| Change | Typical missing facts (ask only these) |
|---|---|
| New job | Company, title (original wording), start month, location; then 1–3 achievements later |
| Job ended | End month; optionally the best result in that role |
| Promotion / new title, same company | New title, start month; keep the role, add a sub-entry or update the title per the user's preference |
| New certification | Exact name, issuer, issue month, expiry |
| New degree / course finished | Original name, institution, end date, official duration |
| New language level or test | Language, test, score, date |
| Moved / new contact details | City, country; work authorization in new markets |
| New target market | Market code → run the market's interview questions only |
| Credential assessment received | Organisation, result as written, reference, issue date |

Ask at most **2–3 questions**, one per message, each with a recommended answer. Everything else stays as it is.

## 2. Apply

1. Update the master profile following `master/schema.md`; bump `last_updated`.
2. **Resolve new equivalences** for new titles or degrees, for every target market (`references/equivalences.md`). A new credential assessment replaces looked-up degree equivalences for its markets.
3. Re-check consistency: overlapping dates, a "present" role that should have ended, achievements now in the wrong role.

## 3. Report stale outputs

List every entry in `outputs` generated before this update that the change affects (all CVs for a new job; only the relevant markets for a new market or assessment), using `messages.md#generate.stale`, and offer to regenerate them. Applications already sent are listed but not regenerated unless asked.

## 4. Proactive check

At the start of a session, if `last_updated` is older than 3 months (`SKILL.md`), ask `questions.md#update.what`. A "nothing new" answer bumps a `last_checked` date in the front matter, not `last_updated`.

## Example

```
User: I passed the CKA last week.

Skill: Congrats! I'll add it. Just two things:
       What date is on the certificate, and when does it expire?
       Recommended: issued 2026-09, expires 2028-09 (CKA is valid for 2 years) — reply "ok" if right.

User: ok

Skill: Added "Certified Kubernetes Administrator (CKA) — The Linux Foundation, 2026".
       These outputs are now out of date: markets/ca-en/cv.md, markets/us-en/cv.md.
       Regenerate them?
```

The validity in the example is illustrative; always confirm expiry with the user or the issuer.
