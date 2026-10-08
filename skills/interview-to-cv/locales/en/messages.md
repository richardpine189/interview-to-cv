# Messages (en)

Fixed user-facing texts. The skill uses them verbatim (filling `{…}`), so their meaning stays the same across sessions and translations. Each block is referenced by its id, e.g. `messages.md#letter.warning`.

---

## Privacy

### privacy.folder
Your profile is stored in `my-cv/`. It contains personal data — keep this folder private and **never** push it to a public repository.

### privacy.claude_ai
I can't keep files between conversations here. At the end of this session I'll give you the updated `master.md` (or the whole `my-cv/` folder as a zip). Save it and attach it next time.

## Interview

### interview.intro
I'll ask you one question at a time, each with a recommended answer — reply "ok" to accept it, write your own, or "skip". I won't ask anything I can already read from your CV.

### interview.progress
{done} of about {total} questions done. You can stop anytime; I'll save what we have.

## Equivalences

### equivalence.disclaimer
These equivalences are guidance based on official classifications and current job postings — not a formal credential assessment.

## Credential recognition

### cred.recommend
You don't have a {assessment name} yet. For {market name} it's {purpose}. You can start it here: {official link}. Until then, your CV shows your degree with its original name and a neutral description.

### cred.expiring
Your {assessment name} from {organisation} expires on {date}. {validity note}

## Cover letters

### letter.warning
⚠️ **Review this letter twice before sending it.** I wrote it from your profile and the job posting, but you know things I don't. Check every fact, every name and every number, and make sure it sounds like you.

### letter.generic_found
These phrases are very common in cover letters and make yours sound like everyone else's:
{list of phrases with their line}
Replace each one with a specific fact, or delete it.

### letter.any_company
Paragraph {n} could be sent to any company. Add something only true of {company}, or cut it.

### letter.checklist
Before you send it:
- [ ] The company name, job title and contact name are correct and spelled right.
- [ ] Every number and achievement is true and you can talk about it in an interview.
- [ ] The "why this company" fact is accurate and current.
- [ ] It fits on one page and has no placeholder left (`<<…>>`).
- [ ] It's addressed to a person when the posting gives a name.
- [ ] You read it aloud once.

### letter.empty_slot
I need one more thing for paragraph {n}: {slot description}. If you don't have it, I'll leave the slot marked instead of filling it with a generic sentence.

## Generation

### generate.done
Your {market name} CV is ready: `{path}`. {ats_result}

### generate.stale
These outputs were generated before your last update and may be out of date:
{list}
Do you want me to regenerate them?

## Freshness

### freshness.market
The rules I have for {market name} were last checked on {date}, more than 6 months ago. Do you want me to check for changes before generating?

### freshness.profile
Your profile was last updated on {date}. Anything new since then — a job, a certification, a move?

## Job matching

### match.never_invent
I won't add experience you don't have. Requirements you don't meet are listed as gaps with a suggestion on how to address them.
