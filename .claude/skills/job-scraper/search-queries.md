# Search Queries for Job Scraper

<!-- Candidate is job-searching in Germany. The built-in scraper CLI tools (Jobindex, Jobnet, Jobbank, Jobdanmark) target the Danish market and are not usable here. -->

## Search Sites

Primary (works out of the box, location-agnostic):
- **linkedin.com/jobs** - LinkedIn job listings, filter to Germany / specific city

Secondary (company career pages via Google `site:` search) - see target companies below.

Planned additions (run `/add-portal` to wire these up as dedicated scraper skills):
- **StepStone** (stepstone.de) - one of the largest German job boards
- **Indeed.de** - broad German job board
- **Xing** - German-market professional network with job listings
- **Arbeitsagentur** (arbeitsagentur.de) - German Federal Employment Agency job board

## Query Categories

Queries are grouped by priority. No commute radius applies - candidate is open to relocating anywhere in Germany or broader Europe, so location terms are broad ("Germany") rather than city-specific.

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

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
