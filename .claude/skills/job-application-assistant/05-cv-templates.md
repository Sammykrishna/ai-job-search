---
framework_version: 1.4.5
---

# CV Templates and Tailoring Guide

<!-- SETUP: Profile statements and section ordering are personalized by running /setup -->

## Template: Two-Column Sidebar (tabular) — DEFAULT, always use this

All CVs use this custom two-column sidebar LaTeX template, dark teal accent color scheme, circular headshot in the sidebar. **This is the standing default for every CV produced by `/apply` — do not fall back to the legacy moderncv template below unless the user explicitly asks for it.**

**Layout mechanism:** a single-row `tabular` of two `p{}` cells (minipages), not `paracol`. The template originally used `paracol` (dynamic two-column balancing), but `pdftotext` testing showed paracol's reflow reordering the underlying PDF text stream once content grew — section headers and their content landed in the wrong place in the extracted text, which breaks ATS keyword parsing even though the visual PDF looks correct. Plain side-by-side minipages (no reflow engine) were tried next, but `pdftotext`'s reading-order heuristic (reconstructs order from text x/y position, not PDF write order) could still braid two independent minipages together when their content reached similar page heights. A single-row `tabular` of two `p{}` cells gives that heuristic a much stronger column-boundary signal and tests cleanly: the sidebar now extracts fully top-to-bottom, then the main column fully top-to-bottom, with no interleaving. The divider between columns is the tabular's own column rule (`colortbl`/`\arrayrulecolor`), not a background overlay.

**Output file:** `cv/main_<company>_<role>.tex`
**Compile with:** **lualatex** (or pdflatex — the template only uses lmodern + T1 fontenc, no fontspec/OpenType fonts) on MiKTeX/TeX Live.
**Page budget:** **exactly 1 page.** This is a single-page, two-column design, not the old 2-page moderncv layout — 1 page is correct and expected; anything else (a near-empty page or spillover to page 2) is a failure that must be fixed.
**Requires:** `cv/proffesional.png` (headshot) in the same directory as the `.tex` file. (An older `cv/proffesional.jpeg` also exists from before the headshot was updated — new CVs should reference the `.png`.)
**Master reference:** `cv/main_mercedesbenz.tex` is the current master copy — start every new CV by copying it verbatim and editing only About Me (see "Section-by-Section Tailoring" below).

### Compile command

```bash
cd cv && lualatex -interaction=nonstopmode main_<company>_<role>.tex
```

Expected output: `Output written on main_<company>_<role>.pdf (1 page, ...)`. Any page count other than 1 is a failure that must be fixed before presenting to the user.

### Layout

- **Left sidebar (6.0cm cell):** circular headshot photo, About Me (profile statement), Education, Personal Data (DOB / Nationality / Location / Work Permit), Languages, Skills (4 category-labeled groups).
- **Right main column (13.9cm cell):** Name + contact header, Work Experience, Projects.
- Dark teal accent color for sidebar headings and job/project titles, dark slate for section headings, a thin vertical divider rule (the tabular's column rule) between the two columns.

### Document structure skeleton

```latex
\documentclass[9pt,a4paper]{article}
\usepackage[a4paper,top=0cm,bottom=0cm,left=0cm,right=0.4cm,nohead,nofoot]{geometry}
\usepackage{graphicx}\usepackage[table]{xcolor}\usepackage{tikz}\usepackage{array}
\usepackage{enumitem}\usepackage[hidelinks]{hyperref}\usepackage[T1]{fontenc}
\usepackage{lmodern}\usepackage{microtype}

% Colours: accentTeal {11,95,97}, jobTeal {15,66,68}, mainHeadCol/sidebarHead {28,47,57}
% Macros: \sideHead{}, \mainHead{}, \jobEntry{title}{org+location}{dates}
% itemize label redefined to plain "-" (ATS-safe, see below)
% Divider: \arrayrulecolor{dividerCol}, drawn as the tabular's own column rule

\begin{document}
\begin{tabular}{@{}p{6.0cm}|p{13.9cm}@{}}
\begin{minipage}[t]{6.0cm}
% LEFT SIDEBAR: photo, ABOUT ME, EDUCATION, PERSONAL DATA, LANGUAGES, SKILLS
\end{minipage}
&
\begin{minipage}[t]{13.9cm}
% RIGHT MAIN COLUMN: name header, WORK EXPERIENCE, PROJECTS
\end{minipage}
\end{tabular}
\end{document}
```

Copy the full preamble (colours, macros, `\setlist` block) verbatim from `cv/main_mercedesbenz.tex` rather than retyping it — it is identical across every CV using this template.

### ATS-safe conventions (critical — do not deviate)

- **All bullet labels and date-range/compound-word separators use a plain ASCII `-`, never `--` (LaTeX en-dash).** This was a confirmed, previously-hit ATS defect: LaTeX `--` under this template's font setup extracts as a `�` replacement character in `pdftotext` (e.g. `2025--Present` extracted as `2025�Present`, corrupting every date on the CV). Always write `03/2025 - present`, `Inactive-Warning-Braking`, `Lishtong - Apple iPhone Manufacturing`, etc. with a single hyphen.
- The `itemize` label is already redefined to a plain `-` via the `\setlist` block in the preamble — never override this back to a bullet glyph or `\textbullet`.

### Section-by-Section Tailoring

**Only the About Me section is tailored per posting. Every other section (Education, Personal Data, Languages, Skills, Work Experience, Projects) is copied unchanged from the master (`cv/main_mercedesbenz.tex`) — no reordering, no reframing, no bullet trimming per job.** This is a standing preference: previous applications reordered Skills and Projects by relevance and reframed Work Experience bullets per posting, but the user found this made every CV inconsistent and asked to simplify to "only About Me is enough for every job." Do not revert to the old per-posting reordering/reframing behavior.

**About Me (sidebar profile statement):** 5-7 short lines, kept simple (short, plain sentences — not dense with jargon or reworked project detail). Always keep the opening sentence establishing hardware + software breadth ("M.Sc. Mechatronics student passionate about robotics across both hardware and software. Designs embedded systems from scratch... and builds ROS2-based perception and manipulation pipelines...") — never drop this framing, since the user explicitly asked to always keep mentioning both hardware and software skills here. The only line that changes per posting is the closing sentence, which should state interest in the specific role/company plainly, e.g. "Interested in the robot-based grasping internship at Mercedes-Benz." Do not rewrite the rest of the paragraph to chase posting keywords.

**Skills (sidebar):** 4 category-labeled groups (bold teal label + comma-separated items beneath), fixed order (Computer Vision / AI, Robotics & Autonomy, Embedded Systems, Tools & Platforms) — do not reorder per posting.

**Education (sidebar):** all three degrees, unchanged across applications — dates, institution, grade.

**Personal Data (sidebar):** DOB, Nationality, Location, Work Permit — unchanged across applications.

**Work Experience (main column, `\jobEntry` + itemize):** same 3 roles reverse-chronological, unchanged bullets across applications.

**Projects (main column, `\jobEntry` + itemize):** all 5 projects, always, in fixed date-order (most recent first) — do not reorder by relevance or trim bullets per posting.

### Compile-and-Inspect Loop (MANDATORY)

After writing the CV and before presenting to the user, always compile and visually inspect the PDF. Because this is a single-page two-column layout, "orphaned entry" (the classic moderncv failure) is not the risk here — the real risks are:

1. **Overflow past the page bottom.** Content that doesn't fit will be silently cut off or overlap the page edge rather than flowing to a second page. Always visually inspect both columns' bottom edges — don't just trust that "it compiled" means it fits.
2. **Visible column imbalance.** One column running noticeably shorter than the other, leaving a large blank gap at the bottom of the shorter side while the other looks packed.

Workflow:
1. Run `lualatex -interaction=nonstopmode main_<company>_<role>.tex`.
2. Check the output page count: must be exactly 1.
3. Read the PDF via the Read tool and visually inspect the full page.
4. If content overflows or a column is packed too tight: cut using **relevance-weighted cutting** below.
5. If there's a lot of trailing white space at the bottom of both columns: the CV looks thin — consider restoring a previously-cut project, or lengthening a short bullet with a concrete detail.

### LaTeX Special Characters (important)

Postings and profile data arrive as plain text; the CV is LaTeX. Escape these wherever they land in body text - company names, achievement bullets, skill lists:

| Character | Write | Typical trigger |
|---|---|---|
| `&` | `\&` | company names: Bang \& Olufsen, Brüel \& Kjær, H\&M |
| `%` | `\%` | quantified achievements: "cut latency by 40\%" |
| `$` | `\$` | salary and cost figures |
| `#` | `\#` | "ranked \#1", C\# |
| `_` | `\_` | file names, code identifiers |
| `~` | `\textasciitilde{}` | URLs, "approx. 5 years" tildes |
| `^` | `\textasciicircum{}` | version strings, math |

Two failure modes deserve special care:

- **`%` fails silently.** An unescaped `%` starts a LaTeX comment: the compile succeeds with zero errors, and everything after the `%` on that line vanishes from the PDF. `Cut inference latency by 40% and saved DKK 2M annually` renders as "Cut inference latency by 40" - the bullet keeps its impressive-looking fragment and loses the actual result. Quantified achievement bullets are exactly where the guidance steers you ("use numbers where possible"), so check every `%` in every bullet before compiling.
- **`&` fails loudly** inside `\jobEntry` (alignment-tab errors, `Missing } inserted`). The compile loop catches it, but escape employer names up front rather than debugging the compile.

Related trap: a bullet whose text begins with a literal `[` must be braced - `\item {[text]}` - or LaTeX parses the bracketed text as `\item`'s optional label and renders it clipped off the left page edge with a clean compile. The example CV's placeholder bullets are braced for exactly this reason.

## ATS Parseability

Most employers run CVs through an ATS before a human sees them, and the ATS reads the PDF's embedded **text layer**, not the rendered page. After the layout passes the compile-and-inspect loop, verify the text layer:

```bash
python tools/verify_pdf.py cv/main_<company>_<role>.pdf --dump-text cv/main_<company>_<role>.txt
```

Extraction tries **pypdf** first (`pip install pypdf`, BSD license), then Poppler `pdftotext`. If a fallback still uses `pdftotext -layout`, it must also pass `-enc UTF-8`: Xpdf-based builds default to Latin-1, which makes every non-ASCII character in a perfectly good CV read back as a replacement character. If neither extractor is available, skip the mechanical check with a warning and rely on the visual PDF read for keyword coverage.

What to check in the extraction:

- **No `--` garbling.** Search the extracted text for `�` — under this template, that character has previously indicated a LaTeX `--` en-dash that failed to get a Unicode mapping (see "ATS-safe conventions" above). If found, grep the `.tex` source for `--` and replace every occurrence with a plain `-`, then recompile and re-extract.
- **Contact details as literal text.** The header prints the email and phone as visible text beside a mobile-icon glyph; the glyph itself may extract as an icon-font name (harmless noise), but the actual address and number must be present as literal text.
- **No other garbled output.** `(cid:NNN)` markers mean a font is embedded without a Unicode mapping.
- **Reading order.** Confirmed clean with the tabular layout: the sidebar extracts fully top-to-bottom, then the main column extracts fully top-to-bottom, with no interleaving between columns. This was the specific defect the paracol-to-tabular migration fixed — if a future edit to the template reintroduces interleaving, that is a regression to flag, not an accepted trade-off.
- **Keyword coverage.** Match the posting's required/preferred terms against the extracted text, in the posting's language. Since About Me is now the only section tailored per posting, keyword coverage will naturally be thinner than under the old fully-reframed workflow — report genuine gaps honestly rather than trying to backfill keywords into sections that are no longer edited per job.
- **Date ranges are ASCII hyphens.** Run `python tools/verify_pdf.py cv/main_<company>_<role>.pdf --ascii-dates` - it exits 1 if any year is joined to a Unicode dash (en-dash U+2013 etc.), which many ATS parsers fail to read as a range. The `--` rule above already prevents this; the script confirms it.

## Page Budget - Hard 1-Page Limit

Since only About Me changes per posting, page fit is essentially fixed by the master template and should not vary between applications. If a future About Me edit is long enough to threaten the 1-page budget, shorten that paragraph rather than touching any other section.

| Section | Budget |
|---------|-----------|
| About Me (sidebar) | 5-7 short lines; only the closing sentence changes per posting |
| Skills (sidebar) | 4 categories, fixed order and content |
| Education (sidebar) | 3 entries, unchanged |
| Personal Data + Languages (sidebar) | unchanged |
| Work Experience (main) | 3 roles, unchanged bullets |
| Projects (main) | all 5 projects, fixed date-order, unchanged bullets |

**If in doubt, cut rather than squeeze.** Do not shrink font sizes or geometry margins below what's already set in the template to force-fit content.

---

## Legacy Template: LaTeX moderncv (Banking Style)

**Only use this if the user explicitly asks for the old 2-page moderncv format instead of the default two-column sidebar template above.** All CVs prior to the two-column sidebar template becoming the default used this format; `cv/main_example.tex` remains a comprehensive reference.

**Compile with:** lualatex. **Page budget:** exactly 2 pages.

```bash
cd cv && lualatex -interaction=nonstopmode main_<company>_<role>.tex
```

### Document Structure

```latex
\documentclass[11pt,a4paper,sans]{moderncv}
\moderncvstyle{banking}
\moderncvcolor{blue}

\renewcommand*{\firstnamestyle}[1]{{\fontsize{34}{36}\bfseries\upshape\color{color1}#1}}
\renewcommand*{\lastnamestyle}[1]{{\fontsize{34}{36}\bfseries\upshape\color{color1}#1}}
\renewcommand*{\sectionstyle}[1]{{\sectionfont\color{color1}#1}}

\usepackage[utf8]{inputenc}
\usepackage{hyperref}
\hypersetup{colorlinks=true,linkcolor=blue,filecolor=magenta,urlcolor=blue,
    pdftitle={[YOUR_NAME] - CV},pdfpagemode=FullScreen}
\usepackage[scale=0.77]{geometry}
\usepackage{import}

\name{[FIRST_NAME]}{[LAST_NAME]}
\address{[YOUR_ADDRESS]}{}{}
\phone[mobile]{[YOUR_PHONE]}
\email{[YOUR_EMAIL]}
\extrainfo{\href{[YOUR_LINKEDIN_URL]}{LinkedIn}, \href{[YOUR_GITHUB_URL]}{GitHub}}

\begin{document}
\makecvtitle
% Profile statement, Core Competencies, Professional Experience, Selected
% Projects, Education, Languages, References
\end{document}
```

Note: on lualatex+MiKTeX, the three `\renewcommand*` overrides are required or firstname/lastname/section headings render black instead of blue. If reviving this template, **also fix the same `--` en-dash ATS-garbling issue described above** — it applies to moderncv date ranges (`\cventry{2025--Present}...`) exactly as it does to the sidebar template; use plain `-` there too.

Do not place `\vspace{...}` between `\item` entries in an `itemize` list (produces oversized gaps) — use the list's native `\itemsep` instead.

If reusing this template, apply `\usepackage{needspace}` sparingly: only immediately before a `\cventry` that is actually at risk of an orphaned title, never proactively before every entry — over-applying `\needspace` has previously caused premature page breaks with large blank gaps rather than preventing orphans.
