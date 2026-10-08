# Workflow: freshness review

Market rules, credential-recognition bodies and classifications change. Every market and reference file carries `last_verified`; this workflow re-checks one file against its sources (DESIGN §15).

## When

- Before generating for a market whose `last_verified` is older than **6 months** — offer it with `messages.md#freshness.market`. The user may decline and generate anyway; then add a one-line note to the output summary that the rules were last checked on that date.
- When `references/classifications.md` is older than 6 months and a new equivalence is being resolved.
- When the user asks ("are these rules still current?").
- Maintainers: when the semi-annual GitHub issue opens (`.github/workflows/standards-review.yml`).

Requires web access. Without it, say so and continue with the stored rules, stating their date.

## Steps

For the market file being reviewed:

1. **Re-open every source** in its `sources` list. Note any that moved, disappeared or changed content.
2. **Check what tends to change**, in this order:
   - credential recognition: organisations, designations, validity periods, fees, processing times, official links;
   - occupation classification versions (e.g. a new NOC, SOC, OSCA or ESCO release) — update `references/classifications.md` too;
   - legal or official guidance on personal data in applications;
   - official CV guidance (length, sections, photo, references);
   - protected-title rules.
3. **Search for news** since `last_verified` on the market's credential body and classification owner ("<body> changes <year>").
4. **Prefer primary sources** (government, regulator, classification owner). Use secondary sources only to find primary ones; never as the only support for a rule.
5. **Propose the diff**: list each change with old value, new value and source. Apply it after the user (or maintainer) agrees.
6. **Update metadata**: `last_verified` to today, `checked` dates on each source that was re-opened, and add new sources.

## In a user session

A user's local copy of the skill may be read-only or reinstalled later. Apply verified changes for the current session (state them in the summary) and tell the user the skill's repository may already have an update. Never silently change rules: every difference is shown with its source.

## For maintainers

In the repository, each reviewed file is one commit: `chore: re-verify <code> market rules (<yyyy-mm>)`, listing the changes in the body. Close the semi-annual issue when every box is ticked.
