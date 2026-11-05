# Organisational deployment

Load only when an organisation (university, career service, training provider, public employment service) runs the skill for many people. Individual use needs none of this.

## 1. Governance (in addition to SKILL.md Section 6)

- Explicit, withdrawable consent before analysis; a consent record per person.
- Involve the organisation's data protection officer before any pilot; define retention with them.
- Pseudonymous IDs in all reports and tables; identity mapping stored separately with access control.
- Human review of every report before release in the pilot.
- Guidance only: never connect outputs to admissions, grading, hiring, promotion or termination decisions (AI Act Annex III, points 3 and 4 [S18]).
- Aggregated reporting only from anonymised data with a minimum group size.

## 2. Pilot (minimum viable product)

| Item | Proposal |
|---|---|
| Users | Advisers run and review reports; participants receive them and can correct their profile |
| Scope | One cohort or group, 15–30 consenting participants, 30–50 real postings, English and French |
| Inputs | Posting, career stage, CV and evidence files, consent record |
| Outputs | HTML report; structured records (Section 3); checklist result |
| Storage | Access-restricted folder per person; one spreadsheet or SQLite file (free) |
| Out of scope | Paid data sources, automatic import from internal systems, numeric scores, self-service web app |

**Phases**

| Phase | Duration | Exit criterion |
|---|---|---|
| 0 — Desk test | 2–3 weeks, synthetic or volunteer profiles | All critical checklist items pass on 10 consecutive reports |
| 1 — Pilot | 6–8 weeks | Success metrics met or explained |
| 2 — Extension | One year | Approval by the service, DPO and management |

**Success metrics** (targets to agree; baselines measured, not assumed): critical errors in shared reports (0); adviser–system agreement on explicit requirements (≥ 80%); company claims with source and date (100%); adviser time per report (below baseline); share of participants who can state their top 3 priorities after reading; usefulness survey (1–5).

## 3. Data model (logical)

| Entity | Key fields |
|---|---|
| person | person_id (pseudonymous), career stage, background field, language, consent_id |
| consent | consent_id, person_id, scope, granted, withdrawn |
| evidence_item | evidence_id, person_id, type, title, date, file reference, verification level |
| skill | skill_id, name, layer, ESCO URI |
| competency / competency_component | competency_id, role, name, definition; skill links |
| company / company_fact | company_id, register ID, country, sector; fact, type, source_id, date |
| job_posting / job_requirement | job_id, URL, retrieval date, raw text; req_id, skill_id, competency_id, origin, status, rule, target |
| assessment / competency_assessment | per requirement and competency: evidence_ids, label, levels, gap, confidence, status |
| recommendation | action, resource, hours, start week, deliverable, criterion, priority |
| source | source_id, URL, publisher, dates, licence |
| report | report_id, version, data block (JSON), checklist result, reviewer, release date |
| audit_log | user, action, object, timestamp |

Withdrawal of consent stops processing and deletes non-anonymised records.

## 4. Value to the organisation

| Stakeholder | Value | Evidence |
|---|---|---|
| Advisers | Consistent, personalised preparation at scale; review instead of writing | Time per report; people served |
| Participants | Clear view of fit, a prioritised plan, honest applications | Clarity and usefulness surveys; self-reported outcomes |
| Programme or curriculum owners | Anonymised view of skills employers ask for vs what is taught | Demand vs learning-outcome mapping |
| Quality and accreditation | Documented evidence for continuous improvement; AACSB Standard 5 expects schools to show how curriculum improved through assurance of learning ("closing the loop") [S11] | Documented improvement actions |
| Employer relations | Reusable, sourced company profiles; hiring-demand trends | Company records |

Do not claim better placement outcomes without a comparison design and enough data. The tool supports advisers; it does not replace them.

[S11] [AACSB — Guiding principles and standards](https://www.aacsb.edu/educators/accreditation/accreditation-process/resources/guiding-principles-and-standards)
