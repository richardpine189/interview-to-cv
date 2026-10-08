---
code: latam-es
name: Latinoamérica (español)
family: latam-cv
template: templates/latam-cv.md
language: es-419
last_verified: 2026-10-07
sources:
  - title: "Dirección del Trabajo (Chile) — no discriminación en ofertas de trabajo (Código del Trabajo, art. 2)"
    url: https://www.dt.gob.cl/portal/1628/w3-article-95023.html
    checked: 2026-10-07
  - title: "Argentina.gob.ar — Convalidá tu título universitario extranjero"
    url: https://www.argentina.gob.ar/educacion/tramites/convalidaciones-universitarias-extranjeros
    checked: 2026-10-07
  - title: "SEP (México) — DGAIR: revalidación de estudios de tipo superior"
    url: https://dgair.sep.gob.mx/dir/revalidacion_superior
    checked: 2026-10-07
  - title: "Ministerio de Educación Nacional (Colombia) — Convalidación de títulos de educación superior obtenidos en el exterior"
    url: https://sedeelectronica.mineducacion.gov.co/SedeElectronica/en/es/tramites/convalidacion-de-titulos-de-educacion-superior
    checked: 2026-10-07
  - title: "ChileAtiende — Reconocimiento de títulos profesionales obtenidos en el extranjero"
    url: https://www.chileatiende.gob.cl/fichas/2461-reconocimiento-de-titulos-profesionales-obtenidos-en-el-extranjero
    checked: 2026-10-07
  - title: "SUNEDU (Perú) — actualización del reglamento de reconocimiento de grados y títulos extranjeros (2026)"
    url: https://www.gob.pe/institucion/sunedu/noticias/1402273-sunedu-actualiza-el-reglamento-para-el-reconocimiento-de-grados-y-titulos-extranjeros
    checked: 2026-10-07
  - title: "SNIEG/INEGI (México) — Acuerdo SINCO 2019"
    url: https://www.snieg.mx/Documentos/Normatividad/Vigente/FT_Tecnica/2.FT_Acuerdo_SINCO.pdf
    checked: 2026-10-07
  - title: "DANE (Colombia) — Clasificación Única de Ocupaciones para Colombia (CUOC)"
    url: https://www.dane.gov.co/index.php/sistema-estadistico-nacional-sen/normas-y-estandares/nomenclaturas-y-clasificaciones/clasificaciones/clasificacion-unica-de-ocupaciones-para-colombia-cuoc
    checked: 2026-10-07
---

# Market: Latin America, Spanish (`latam-es`)

One market for all Spanish-speaking Latin American countries (DESIGN §6). Country-specific vocabulary and credential recognition are applied when the user names a target country; the CV rules are the same everywhere.

## Why one conservative rule set

Older CVs in the region carried a photo, date of birth, national ID and marital status. Hiring practice has moved away from requesting them, and several countries restrict discriminatory requirements in job offers — Chile's Dirección del Trabajo, for example, supervises offers that require a photo, a specific age or "buena presencia" under art. 2 of the Código del Trabajo. This market therefore follows the most conservative rule in every country.

## Include

- Name, city and country, phone in international format, email, LinkedIn; GitHub or portfolio for technical roles.
- Optional headline with the target role.
- Perfil profesional, Experiencia laboral, Formación académica, Habilidades, **Idiomas** (always), Certificaciones; Proyectos optional.
- **Work authorization:** one line only when the user is applying to a country where they are not a citizen and already holds a permit, e.g. « Residencia permanente en Chile ».

## Omit

Always, in every country:

- photo
- age or date of birth
- national ID number (DNI, CURP, RUT, RUN, cédula, CUIL/CUIT)
- marital status, children, gender
- nationality, place of birth
- full street address (city and country are enough)
- references (on request)
- salary expectations, unless the posting asks — then in the letter or the application form, not on the CV

If a posting explicitly asks for one of these, the user can add it to the application form; the CV stays clean.

## Transform

| Element | Rule |
|---|---|
| Language | Neutral Latin American Spanish. When the user names a country, use its terms: *hoja de vida* (CO), *currículum* (MX, AR, CL), *celular*, *licenciatura* (MX, AR), *pregrado* (CO), *título profesional* (CL, PE). Use *usted* in letters. |
| Bullets | Past tense for past roles, present for the current one; impersonal or first person without the pronoun (*Reduje…*, *Lideré…*). Quantified where possible. |
| Dates | `abr. 2021 – actualidad`; education: year only. |
| Section names | Perfil profesional · Experiencia laboral · Formación académica · Habilidades · Idiomas · Certificaciones · Proyectos |
| Language levels | Words + CEFR code: *Nativo* / *Bilingüe (C2)* / *Avanzado (C1)* / *Intermedio-avanzado (B2)* / *Intermedio (B1)* / *Básico (A1–A2)*. Add certificates (TOEFL, IELTS, Cambridge, EF SET) with score. |
| Job titles | `equivalences.latam-es.chosen`. Use *Ingeniero/a* only when the user holds an engineering degree: in much of the region it is a professional title tied to the degree and, in some countries, to registration with a professional body. Prefer *Desarrollador/a*, *Programador/a*, *Analista*, *Arquitecto/a de software*. English titles (*Software Engineer*, *Tech Lead*) are common in regional tech postings; ask which language the posting uses. |
| Degrees | When a recognition exists (convalidación, revalidación, reconocimiento), name it. Otherwise original name + duration + country. Map to *licenciatura / título de grado / pregrado* or *maestría / posgrado* only when duration and access requirements support it. |
| Numbers | Follow the target country: `1.200` (AR, CL, CO) or `1,200` (MX, PE in many contexts); state the currency (`USD`, `ARS`, `MXN`…). |
| Company and institution names | Never translated. |

## Constraints

| Constraint | Value |
|---|---|
| Length | 1 page for early career; 2 pages maximum. |
| Bullets per role | 3–5 for recent roles, 1–2 for older ones. |
| Years shown | Last 10–15 years in detail. |
| Carta de presentación | Optional in many postings; generate when asked or when the posting requests it. |

## Section names (for the template)

```yaml
section_names:
  profile: Perfil profesional
  experience: Experiencia laboral
  education: Formación académica
  skills: Habilidades
  languages: Idiomas
  certifications: Certificaciones
  projects: Proyectos
  cover_letter: Carta de presentación
  salutation: Estimado equipo de selección:     # « Estimada Sra. X: » / « Estimado Sr. Y: » when the name is known
  closing: Quedo a su disposición para conversar en una entrevista.
  sign-off: Saludos cordiales,
```

## Occupation sources

National classifications are adaptations of ISCO-08 (CIUO-08); query the one for the target country, with ISCO-08 as the default:

| Country | Classification | Owner |
|---|---|---|
| Mexico | SINCO 2019 | INEGI |
| Colombia | CUOC (replaced CIUO-08 A.C. in 2021) | DANE / Ministerio del Trabajo |
| Chile | CIUO-08.CL | INE |
| Argentina | CNO (adopted by INDEC in 2018) | INDEC |
| Other / several countries | CIUO-08 (ISCO-08) | ILO |

Validate wording against current postings in the target country (official employment services, Computrabajo, Bumeran, OCC, elempleo) and regional tech job boards.

## Credential recognition

Recognition of foreign degrees is national. Ask only for the countries the user targets.

```yaml
credential_recognition:
  required_for_migration: false   # usually needed for regulated professions and public employment, not for private IT jobs
  by_country:
    AR:
      assessment: Convalidación (countries with a reciprocity agreement) or reválida (others, at a national public university)
      url: https://www.argentina.gob.ar/educacion/tramites/convalidaciones-universitarias-extranjeros
      notes: Agreement list on the page (e.g. Bolivia, Chile, Colombia, Ecuador, Spain, Mexico, Peru); filed online through TAD.
    MX:
      assessment: Revalidación de estudios (SEP — DGAIR), then title registration and cédula profesional if needed
      url: https://dgair.sep.gob.mx/dir/revalidacion_superior
      notes: Studies must have official validity in the country of origin.
    CO:
      assessment: Convalidación de títulos de educación superior (Ministerio de Educación Nacional)
      url: https://sedeelectronica.mineducacion.gov.co/SedeElectronica/en/es/tramites/convalidacion-de-titulos-de-educacion-superior
      notes: 100 % online, individual analysis; documents apostilled or legalised. Homologación is a different process done by universities.
    CL:
      assessment: Reconocimiento de títulos — Ministerio de Relaciones Exteriores (agreement countries), Mineduc (e.g. Argentina, Spain, UK) or Universidad de Chile (others)
      url: https://www.chileatiende.gob.cl/fichas/2461-reconocimiento-de-titulos-profesionales-obtenidos-en-el-extranjero
      notes: The route depends on the issuing country; check the current list.
    PE:
      assessment: Reconocimiento de grados y títulos extranjeros (SUNEDU)
      url: https://www.gob.pe/institucion/sunedu/noticias/1402273-sunedu-actualiza-el-reglamento-para-el-reconocimiento-de-grados-y-titulos-extranjeros
      notes: Regulation updated in June 2026; practising a profession is enabled by the professional association (colegio), not by SUNEDU.
  purpose: >
    Gives the foreign degree official validity in the country. Private IT employers
    rarely require it; it is needed for regulated professions (engineering with
    professional registration, health, law…), public employment and further study.
  validity: No expiry stated on the pages verified.
  when_to_ask: >
    Ask once per target country, only when the user studied outside it. If no,
    mention the process as optional for private IT jobs and recommend it for regulated
    professions, public employers or postgraduate study, with the official link.
```

Countries not listed: tell the user recognition is handled by the country's education ministry and recommend checking its official site; do not guess the procedure.
