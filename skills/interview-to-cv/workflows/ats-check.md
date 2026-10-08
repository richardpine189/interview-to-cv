# Workflow: ATS check

Applicant tracking systems parse a CV into fields (name, contact, roles, dates, education, skills) before a person reads it. Parsing fails silently: a field the parser misses is a field the recruiter's search never finds. This check runs on **every generated CV** (DESIGN §11) and on custom templates before filling them.

## When

- After step 4 (Generate) of `SKILL.md`, for each market output.
- Before filling a custom template (`workflows/custom-templates.md`).
- On demand: "is my CV ATS-friendly?" — run it on the user's own file.

## Checks

Report each as ✅ pass, ⚠️ warning or ❌ fail, with the line or element and a fix.

| # | Check | Fail when | Fix |
|---|---|---|---|
| 1 | Single column | Text is laid out in two or more columns, or sidebars | Move sidebar content (skills, languages) into normal sections |
| 2 | No tables for layout | Roles, dates or skills are inside tables | Plain lines and bullets |
| 3 | Nothing important in header/footer | Name, contact or dates only exist in the document header/footer | Put them in the body |
| 4 | No text in images, icons or charts | Skill bars, rating dots, logos with text, icons replacing words (☎ instead of "Phone") | Words instead of graphics; levels as text |
| 5 | Standard headings | Creative headings ("My journey", "What I bring") | Use the market's `section_names` |
| 6 | Parseable dates | Missing months on recent roles, mixed formats, ranges like "'21–'23" | The market's date format, consistently |
| 7 | Contact details as text | Email/phone only as hyperlinks or images | Plain text, one line |
| 8 | Text-based PDF | Exported PDF is an image (scanned or flattened) | Export from the source; never "print to image" |
| 9 | Standard fonts and characters | Decorative fonts, ligatures, special bullets that become `?` | Common fonts; `-` or `•` bullets |
| 10 | Keywords present (job mode only) | A must-have keyword from the posting is missing where the user has the skill | Add the exact wording from the posting in skills or a bullet — never for skills the user lacks |
| 11 | File name | `cv.pdf`, `final_v3.pdf` | `Given-Family-CV-<market>.pdf` |
| 12 | Length and density | Over the market limit, or walls of text over 5 lines | Apply the market's constraints |

Checks 8, 9 and 11 apply to exported files; run them in the export workflow.

## Output

```
ATS check — ca-en CV
✅ Single column · ✅ No tables · ✅ Header/footer · ✅ No graphics · ✅ Headings
⚠️ Dates: "2019 – 2020" at Contoso has no months → use "Mar 2019 – Nov 2020"
❌ Keywords: the posting asks for "Kubernetes"; your profile lists it but the CV doesn't show it → added to Skills
Result: 1 fixed automatically, 1 needs your input.
```

Fix what can be fixed without new facts; ask the user for the rest. Never add a keyword for a skill the master profile does not support.

## ATS layout

When the user asks for an "ATS version", produce the market template with:

- no bold company lines, separators or emphasis beyond headings;
- one line per contact item allowed, still in the body;
- skills as comma-separated lists;
- the same content and order as the standard version.

The built-in templates are already single-column and table-free, so the ATS layout differs only in emphasis.
