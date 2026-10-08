---
last_verified: 2026-10-07
sources:
  - title: "Europass — FAQ (importing CVs: only Europass-generated PDF+XML or XML)"
    url: https://europass.europa.eu/en/faq?page=1
    checked: 2026-10-07
  - title: "Europass — Interoperability (CV editor accepts XML or PDF+XML uploads)"
    url: https://europa.eu/europass/en/europass-interoperability
    checked: 2026-10-07
  - title: "Europass — CV editor"
    url: https://europa.eu/europass/eportfolio/screen/cv-editor
    checked: 2026-10-07
---

# Workflow: export

Turns a generated Markdown CV or letter into the format the user needs (DESIGN §14). The Markdown file in `my-cv/` stays the source; exports are regenerated from it, never edited by hand.

Ask which format, with a recommended answer: **PDF** for applying by email or portal, **Word** when a recruiter asks for an editable file.

| Format | Output | Use |
|---|---|---|
| Markdown | `cv.md` (already exists) | Source, version control, pasting |
| Word | `cv.docx` | Recruiters who edit CVs; company templates |
| PDF | `cv.pdf` | Applications by email or upload |
| ATS-safe | `cv-ats.docx` + `cv-ats.pdf` | Portals with strict parsers |
| XeLaTeX | `cv.tex` | Users who want typographic control |
| Europass | Content sheet for the Europass editor | EU applications that ask for Europass |

File names follow the ATS check (#11): `Given-Family-CV-<market>.<ext>`, `Given-Family-Cover-Letter-<company>.<ext>`.

## Word and PDF

Use the tools available in the environment, in this order:

1. **Document skills** provided by the platform (e.g. the docx / pdf skills in Claude.ai and Claude Code) — preferred.
2. **pandoc** if installed: `pandoc cv.md -o cv.docx`; for PDF, `pandoc cv.md -o cv.pdf --pdf-engine=xelatex` or convert the `.docx` with LibreOffice (`soffice --headless --convert-to pdf cv.docx`).
3. **python-docx** / an HTML page printed to PDF with a headless browser, as a last resort.

Layout rules for both:

- A4 for `uk-en`, `au-en`, `fr-fr`, `be-fr`, `latam-es`; US Letter for `us-en`, `ca-en`, `ca-fr`.
- One column; body 10–11 pt in a common font (Calibri, Arial, Helvetica, Georgia, Garamond); margins 1.5–2.5 cm.
- Name as the only large text; headings as real Word heading styles (parsers use them).
- Contact details in the body, not in the header/footer.
- **PDF must be text-based** — verify by extracting the text and checking that name, email and a role title come out in order.
- Custom Word/PDF templates keep their own design (`workflows/custom-templates.md`).

After exporting, re-run ATS checks 8, 9 and 11 on the file.

## ATS-safe

Same content as the market CV with the ATS layout from `workflows/ats-check.md`: no emphasis beyond headings, no separators, skills as comma lists, plain bullets. Export both `.docx` and `.pdf`; portals vary in which they parse better.

## XeLaTeX

Generate a single self-contained `cv.tex`:

- `\documentclass[11pt,a4paper]{article}` (or `letterpaper` per market) with `fontspec`, `geometry`, `enumitem`, `hyperref`, `titlesec` only — no exotic classes, so it compiles anywhere.
- UTF-8 throughout; XeLaTeX handles accents and non-Latin names.
- Escape LaTeX special characters (`& % $ # _ { } ~ ^ \`) in all content.
- One column; same section names and order as the Markdown CV.

If `xelatex` is installed, compile it and check the PDF as above. If not, tell the user how to compile online:

> Open overleaf.com → New Project → Upload Project → choose `cv.tex` → Menu → Compiler: **XeLaTeX** → Recompile → Download PDF.

## Europass

The Europass platform only imports files that Europass itself generated (PDF with embedded Europass XML, or Europass XML); a Word file, or a PDF made from one, is rejected. This skill therefore does **not** produce an importable Europass file. Instead:

1. Produce `europass-sheet.md`: the CV content arranged in the Europass editor's order, in the market language, ready to copy field by field:
   - Personal information (only what the market allows — the editor makes most fields optional),
   - About me,
   - Work experience (one block per role: occupation, employer, city/country, dates, main activities),
   - Education and training (title of qualification, organisation, dates, level if known),
   - Language skills (mother tongue; other languages with CEFR levels for listening, reading, spoken production, spoken interaction, writing),
   - Digital skills, Driving licence (only if relevant), Certifications.
2. Tell the user to open the Europass CV editor (https://europa.eu/europass/eportfolio/screen/cv-editor), create or update a CV and paste each block.
3. Once they download the Europass PDF, it can be re-imported to Europass later; keep the Markdown CV as the source for every other format.

Re-check the import rules at each freshness review; if Europass publishes an import format for external files, this section is the one to change.

## Delivery

- With a file system: save next to the source (`my-cv/markets/<code>/` or the application folder) and record each export in `outputs`.
- Without one (Claude.ai): return the files as downloads and remind the user that the Markdown source and `master.md` are what to keep.
