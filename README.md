# Job Readiness Assessment

An AI skill that tells you, with evidence, how ready you are for a specific job — and what to do about the gaps.

Give it **one job posting** and **one profile** (CV, portfolio, certificates, work history). It analyses the posting and the employer, separates what the job states from what it implies, compares that with what you can actually show, and produces a visual HTML report with a prioritised, week-by-week plan.

It works for **anyone at any career stage** — students, early-career professionals, experienced and senior people, career changers and people returning to work — and in **any field**, in **English or French**.

---

## What it does

| Step | Output |
|---|---|
| Job analysis | Explicit requirements (stated) and implicit requirements (derived by documented rules, always tagged "Inference") |
| Employer research | Company profile from free, citable public sources; each claim tagged Fact (with source) or Analysis |
| Skills and competencies | Universal, background, role-specific and durable human skills, combined into 3–6 role competencies; linked to ESCO where possible |
| Evidence matching | Each requirement rated L1–L4 against a target set by career stage, with an evidence label and a verification level (V0 self-statement → V3 issuer-verified) |
| Plan | Top 3 priorities and a weekly plan with hours, deliverables and completion criteria |
| Report | One self-contained HTML file, dashboard first, details below, exportable to PDF |

## Principles

- **No invented evidence.** Missing evidence is "not assessed", never a weakness.
- **No single score.** Readiness is shown as counts by status.
- **Traceable.** Every recommendation links to a requirement, a cited source, the person's evidence or a labelled inference.
- **Free sources only.** No paid databases; no scraping against site terms.
- **Career stage from experience, never from age.**
- **Licences and regulated qualifications** are treated as required and checked only against the issuer or an official register.
- **GDPR by design:** minimisation, no use of protected characteristics, pseudonymous IDs, right to correct.
- **EU AI Act aware:** guidance for the applicant only. It must not be used to screen, rank or evaluate candidates, or to decide admission or grades — uses the AI Act classifies as high-risk (Annex III, points 3 and 4).

---

## Structure

```
job-readiness-assessment/
├── SKILL.md                      # Core workflow and rules (~10 KB, loaded when the skill triggers)
├── README.md
├── INSTALL.md                    # How to load the skill into Claude or another AI agent
├── references/                   # Loaded only at the step that needs them
│   ├── taxonomy.md               # Skill layers, competencies, implicit-requirement rules, durable human skills
│   ├── sources.md                # Job, labour-market and company sources; verified source list
│   ├── report.md                 # Report layout and data fields
│   ├── quality-checklist.md      # Pass/fail checks before sharing
│   └── deployment.md             # For organisations: pilot plan, data model, value and KPIs
└── assets/
    └── report_template.html      # Report template with a fictional example
```

The core file stays light; detail loads only when a step needs it.

---

## How to use

Full installation steps for the Claude app, Claude Code, the API and other AI agents: **[INSTALL.md](INSTALL.md)**.

1. Add the `job-readiness-assessment` folder as a skill in Claude (Claude Code: place it in `.claude/skills/`; Claude app: upload the zipped folder as a custom skill).
2. Share a job posting (text or link) and your CV or profile. Say your career stage and how much time you have, if you like.
3. Open the HTML report in a browser. **Save as PDF** exports it.

To preview the output, open `assets/report_template.html` in a browser (fictional example).

## For organisations

Universities, career services and training providers can run it for groups of people. `references/deployment.md` covers consent, data-protection officer involvement, a pilot plan, a data model and the value for each stakeholder, including curriculum feedback for accreditation.

## Scope and limits

- Guidance only, not a hiring, admission or grading decision.
- Labour-market sources are French and EU by default; other countries use their own official registers and employment services.
- Does not judge the equivalence of foreign or regulated qualifications; it points to the competent authority.
- Human-centred skills are assessed only from real behavioural examples; wellbeing is never assessed.

---

## Authorship

- **Concept, scope, requirements and review:** Bhavesh
- **Drafting and implementation:** Claude (Anthropic), working from the author's instructions and feedback

The author defined what the skill must cover (minimum viable product, verifiable data sources, databases, implicit and explicit competencies, employer elements, value to the institution, GDPR and AI Act compliance, career-stage coverage) and reviewed each version; Claude wrote the skill files, the report template and the source checks.
