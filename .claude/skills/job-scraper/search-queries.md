# Search Queries for Job Scraper

<!-- Candidate is job-searching in Germany. The built-in scraper CLI tools (Jobindex, Jobnet, Jobbank, Jobdanmark) target the Danish market and are not usable here. -->

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first. Shipped country-agnostic CLIs include `linkedin-search` and `freehire-search`; Danish demos and any skill you add with `/add-portal` are included the same way. You do **not** need a matching `site:` line below for those CLIs to run.

The `site:` query templates in this file are the **WebSearch fallback** — for portals without a CLI, company career pages, or when a CLI fails.

**Language scope:** write every query category in every language listed in your CLAUDE.md Languages table (typically 1-2, sometimes more). A posting requiring a language you have *not* declared, as a job condition, is excluded before scoring; a posting requiring a *higher level* than you declared in a language you *do* work in is flagged for your own judgment, not excluded — see `04-job-evaluation.md`'s Language Gate, the single source of truth for this rule. Translate each category's keywords rather than machine-translating word-for-word (e.g. "Frontend Developer" -> "Desarrollador Frontend", not a literal word-for-word translation) if you work in more than one language.

## Search Sites

Primary (works out of the box, location-agnostic):
- **linkedin.com/jobs** - LinkedIn job listings, filter to Germany / specific city; also covered by `linkedin-search` CLI

Secondary (company career pages via Google `site:` search) - see target companies below.

Planned additions (run `/add-portal` to wire these up as dedicated scraper skills):
- **StepStone** (stepstone.de) - one of the largest German job boards
- **Indeed.de** - broad German job board
- **Xing** - German-market professional network with job listings
- **Arbeitsagentur** (arbeitsagentur.de) - German Federal Employment Agency job board

## Query Categories

Queries are grouped by priority. No commute radius applies - candidate is open to relocating anywhere in Germany or broader Europe, so location terms are broad ("Germany") rather than city-specific.

**Organize by function, not job title.** The same underlying work carries different titles across companies and markets (a "Data Scientist" role at one employer may be posted as "Insights Analyst" or "Data Consultant" at another). Name each priority category after the function it covers, and list several plausible job titles as query variants within that category rather than betting an entire priority tier on one exact title string.

### Priority 1: Robotics Manipulation & Perception

Primary and most desired career direction.

```
site:linkedin.com/jobs "Robotics Engineering Working Student" Germany
site:linkedin.com/jobs "Werkstudent Robotik" Germany
site:linkedin.com/jobs "Computer Vision Working Student" Germany
site:linkedin.com/jobs "Werkstudent Computer Vision" Germany
site:linkedin.com/jobs "Perception Software Engineer" Werkstudent Germany
site:linkedin.com/jobs "Manipulation" "Grasp Planning" Intern Germany
```

### Priority 2: Embedded / Robotics Control

Secondary career direction - embedded systems and robotics control.

```
site:linkedin.com/jobs "Embedded Systems Working Student" Germany
site:linkedin.com/jobs "ROS2" "Robotics Software" Intern Germany
site:linkedin.com/jobs "Embedded Systems" Werkstudent PCB OR Firmware Germany
```

### Priority 3: Autonomous Driving / Sensor Fusion

Third career direction - autonomous driving and sensor fusion.

```
site:linkedin.com/jobs "Autonomous Driving" "Sensor Fusion" Intern Germany
site:linkedin.com/jobs "ADAS" Werkstudent Germany
site:linkedin.com/jobs "Sensor Fusion" "Working Student" Germany
```

### Priority 4: Target Companies (broader net via company career pages)

```
site:neura-robotics.com jobs OR careers Werkstudent OR intern
site:sereact.ai careers
site:zeiss.com careers robotics OR "computer vision" intern
site:bmwgroup.jobs "working student" robotics OR "computer vision"
site:ipa.fraunhofer.de jobs OR karriere
site:cml.fraunhofer.de jobs OR karriere
site:truphysics.com careers
site:liebherr.com careers robotics OR embedded
site:global.abb careers robotics OR embedded intern
```

## Location Filter

No commute constraint - candidate is open to relocating anywhere in Germany, and open to broader Europe. All of Germany, remote, hybrid, and on-site roles are acceptable. No borderline/too-far tiers apply.

## Language Filter

Your working languages and levels are in CLAUDE.md's Languages table. When filtering scraped results, apply `04-job-evaluation.md`'s Language Gate: a posting requiring a language you haven't declared at all is excluded; a posting requiring a higher level than you declared in a language you do work in is not excluded, flag it clearly instead (see `job-scraper/SKILL.md`'s Step 3 "Quick Fit Assessment" for how the flag surfaces in `/scrape` output). Postings simply *written* in a language you don't work in, that don't require it on the job, are fine.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
