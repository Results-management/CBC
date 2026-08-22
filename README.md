# School Results App — CAT + Exam Edition

Adapted from the same base app, with two structural changes:

1. **Every subject is scored as CAT (out of 30) + Exam (out of 70) = Total (out of 100)**,
   for both Mid Term and End Term assessments.
2. **CRE renamed to RE** (Religious Education), since learners follow either CRE or IRE.

Everything else — single-stream or multi-class grades, School Settings, Manage
Classes, Year Advancement Wizard, Excel/CSV, Results Analysis — works the same
as before.

## Files
- `index.html` — the whole app
- `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png` — installable home-screen app (PWA)
- `db.json` — empty starting database

## Upload to GitHub Pages
1. Create a new **public** repo.
2. Upload all six files to the repo root, on the `main` branch.
3. Settings → Pages → Deploy from branch → `main` / `root`.

## First-time setup
1. Open the site → **Database Settings** → enter your GitHub owner, repo name,
   and a Personal Access Token (`repo` scope).
2. Log in: username `admin`, password `admin2026`. **Change this immediately**
   under ✏️ Manage Team.
3. Go to **🏫 School Settings** and fill in your school's header exactly as
   you want it to print — School Name, P.O. Box, County, Motto, Phone, Email.
   Leave any field blank to leave it off the header entirely. This is what
   appears on the login screen, class lists, and report cards:

   ```
   YOUR SCHOOL NAME
   P.O BOX 32 - 80120
   YOUR COUNTY
   Motto: Hard Work Pays
   0712 345 678 · info@yourschool.ac.ke
   ```

4. Go to **🏫 Manage Classes** to set up your grades — add as many named
   classes per grade as you need (or leave the single default "Main" class
   per grade if you don't split streams).
5. Go to **✏️ Manage Team** to set up real logins for your class teachers
   and rename the subject-teacher placeholder accounts below.

## Logins (change all of these before going live)
| Login | Username | Password | Covers |
|---|---|---|---|
| Admin | `admin` | `admin2026` | Everything |
| Mathematics | `mathematics` | `math2026` | Grades 7–9 |
| English | `english` | `eng2026` | Grades 7–9 |
| Kiswahili | `kiswahili` | `kis2026` | Grades 7–9 |
| Integrated Science | `science` | `sci2026` | Grades 7–9 |
| Pre-Technical Studies | `pretechnical` | `pts2026` | Grades 7–9 |
| Agriculture & Nutrition | `agriculture` | `2026agric` | Grades 7–9 |
| Social Studies | `socialstudies` | `ss2026` | Grades 7–9 |
| RE (Religious Education) | `re` | `re2026` | Grades 7–9 |
| Creative Arts & Sports | `creativearts` | `cas2026` | Grades 7–9 |
| Class Teacher, Grade 7/8/9 | `classteacher7`/`8`/`9` | `2026` | One grade each |

## How CAT + Exam works
- **Marks entry** (both the subject-teacher's day-to-day screen and the
  admin's "Edit Learner" tool) shows two boxes per subject: **CAT** (capped
  at 30) and **Exam** (capped at 70, labeled "Mid Term" or "End Term"
  depending which is currently selected).
- The **Total** (CAT + Exam, out of 100) is computed automatically everywhere
  — grading bands, class ranking, class means, subject means, Results
  Analysis — nothing needs to be entered as a single combined number.
- The **report card** shows all three: CAT, the exam score, and Total, per
  subject — matching a physical mark sheet.
- The whole-class list (many learners × many subjects on one page) shows just
  the Total per subject, to keep it printable — the CAT/Exam breakdown is on
  each learner's individual report card.
- **Excel and CSV** exports/imports include CAT and Exam as separate columns
  for every subject (plus a computed Total column), so you can prepare marks
  offline in the same format.

## What every role can do
- **Admin** — everything: connect the database, School Settings, Manage
  Classes, Manage Team, Year Setup, all downloads/prints.
- **Class Teacher** — their assigned grade only: register/edit learners,
  enter marks for any subject if needed, comments, print/download, CSV/Excel.
- **Subject Teacher** — any class, their one subject: CAT/Exam entry, grade
  distribution, print/download for that subject's data.

## Notes
- Data lives in `db.json` in your GitHub repo — every teacher's device stays
  in sync automatically as long as they're connected.
- **⬇ Download buttons now produce real PDF files** (using a client-side PDF
  generator), not HTML. Downloading "All Report Forms" for a full class can
  take a few seconds — the button shows "Generating PDF…" while it works.
  The 🖨 Print buttons still open the browser's print dialog as before,
  which also lets you choose "Save as PDF" if you prefer that route.
- **The "Edit Learner" screen now scrolls properly** — the Save/Cancel
  buttons stay pinned at the bottom while the subject list scrolls above them,
  so they're always reachable on a phone screen.
- **The header no longer adds a redundant "Junior Secondary School" line** —
  it shows exactly what you enter in School Settings (name, P.O. Box,
  county, motto, contact) and nothing else.
- Report cards and class lists print via the browser's Print dialog
  (Print → Save as PDF).
- Never share your GitHub Personal Access Token outside the app's own
  Database Settings screen.
- One GitHub repo = one school. This is a separate deployment from any other
  school's app — its own repo, its own data, its own School Settings.
