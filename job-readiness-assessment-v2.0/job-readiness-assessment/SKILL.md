---
name: job-readiness-assessment
description: Produce an evidence-backed job readiness report for anyone applying to a specific job, at any career stage and in any field. Analyses the job posting and the employer, separates explicit from implicit requirements, maps them to skills and competencies, compares them with the person's verified evidence, and delivers a visual HTML report with a prioritised plan. Use whenever someone shares a job description or job link together with a CV or profile and asks about fit, skills gaps, competencies, readiness, preparation, career change or interview prep, even if the word "report" is not used. Works in English and French.
---

# Job Readiness Assessment

**Version:** 2.0 · **Date:** 2026-11-05

Given **one job posting** and **one person's profile**, produce a readiness report: what the role requires (stated and implied), what the person can show, where the gaps are, and a realistic plan to close them. Works for any career stage (student to senior, career changers, people returning to work) and any field.

This is a guidance tool for the person applying. It is not a hiring, grading or selection tool (Section 6).

## Reference files

Load each file only at the step that needs it.

| File | Load at | Contains |
|---|---|---|
| `references/taxonomy.md` | Steps 4–6 | Skill layers, competency structure and example profiles, durable human skills, implicit-requirement rules |
| `references/sources.md` | Steps 1 and 3 | Job, labour-market and company sources; company profile elements; verified source list |
| `references/report.md` | Step 8 | Report layout, data-block fields, render check, fallback |
| `references/quality-checklist.md` | Step 8 | Pass/fail criteria before sharing |
| `references/deployment.md` | Only for organisational use | Pilot (MVP) plan, data model, retention, value and KPIs for a university, career service or employer-funded programme |
| `assets/report_template.html` | Step 8 | Report template (with a fictional example) |

---

## 1. Workflow

1. **Job posting.** Accept text or a URL. Capture title, employer, location, contract, responsibilities, required and preferred qualifications, tools, languages, and any licence or certification the role requires. Record the source and retrieval date. State what is missing; never fill gaps.
2. **Profile.** Use only the profile provided for this analysis (CV, portfolio, projects, certificates, work history, references, the person's own statements). Record the **career stage** (Section 2). Give each evidence item a verification level (Section 3).
3. **Employer.** Research the company from free, citable sources (`references/sources.md`). Tag each statement **Fact** (with source) or **Analysis**.
4. **Requirements.** Extract explicit requirements, then derive implicit ones with the rules in `references/taxonomy.md`. Classify each as required, preferred or contextual. Implicit requirements are never "required".
5. **Competencies.** Build 3–6 role competencies from the posting's main responsibilities, or use an example profile if one fits. Link every requirement to one competency.
6. **Match.** Rate each requirement against the person's evidence (Sections 3–4). Rate each competency (Section 4.3). Identify transferable evidence, especially for career changers.
7. **Plan.** Rank gaps (Section 4.2). Propose concrete tasks with time, deliverable and completion criterion, sized to the time the person has. Recommend truthful CV positioning.
8. **Report.** Fill the template's data block, deliver the HTML report, then run the quality checklist and fix any failure before sharing.

---

## 2. Career stage and target levels

**Proficiency scale**
- **L1 Foundation:** understands concepts; completes guided tasks.
- **L2 Applied:** completes common tasks independently.
- **L3 Professional:** handles complex tasks, explains decisions, delivers reliably.
- **L4 Advanced:** leads, optimises or innovates in complex situations.
- **Below L1:** the person confirms no exposure yet (never inferred from missing evidence).
- **Not assessed:** not enough evidence to judge. **Not applicable:** irrelevant to the role.

**Career stage.** Determine it from the person's statement or work history, **never from age**.

| Stage | Description | Typical target ceiling |
|---|---|---|
| Student / intern / apprentice | In education or a work-based learning contract | L1–L2 |
| Early career | First roles in the field | L2–L3 |
| Experienced | Established practitioner | L3 |
| Senior / lead | Leads people, programmes or a domain of expertise | L3–L4 |
| Career changer / returner | Moving from another field, or returning after a break | Set from the posting; weight transferable evidence |

Set each target from the posting, then apply the ceiling unless the posting explicitly asks for more. State the reason when a target exceeds the ceiling. The ceilings are this skill's proposal, not an external standard.

---

## 3. Evidence

**Verification levels**

| Level | Meaning | Examples |
|---|---|---|
| **V3** Issuer-verified | Confirmed by the issuing institution, employer or official register | Transcript from the school; signed employer reference; entry in an official professional register |
| **V2** Externally checkable | A third party can check it | Certificate with verification link; public code repository; publication with DOI; public portfolio |
| **V1** Document supplied | Artefact provided, not independently checked | Project report, slides, detailed CV entry, performance review supplied by the person |
| **V0** Self-statement | Claim without artefact | Self-assessment; CV keyword |

**Evidence labels:** Demonstrated (V1+ artefact shows it) · Transferable (related experience, different task or tool) · Self-reported (V0) · Needs verification (ambiguous) · Not evidenced (nothing supplied; not proof of inability).

Rules:
- Verification raises confidence, not proficiency. A CV keyword alone is never proof.
- Never invent experience, tools, qualifications, metrics or levels.
- **Licences and regulated qualifications** (e.g. medical, legal, engineering, teaching, financial certifications): treat them as explicit, required requirements. Record them as met only from an official register or the issuing body (V3) or a supplied document (V1, flagged "verify with issuer"). Never judge whether a foreign qualification is equivalent; point to the competent authority.
- Do not contact third parties without the person's consent.

---

## 4. Matching

### 4.1 Requirement status
**Strong** (meets target, V1+) · **Relevant / transferable** (close to target) · **Partial** (below target) · **Gap** (evidence, including the person's statement, shows it is not there yet) · **Not assessed** (no usable evidence).

No overall percentage or score. Gap = max(0, target − current), calculated only when both levels are known.

### 4.2 Ranking gaps
1. Required by the posting. 2. Importance to the main responsibilities. 3. Size of the gap. 4. Evidence strength. 5. Feasibility in the person's time frame.

### 4.3 Competency status
- **Demonstrated in context:** one V1+ artefact shows the component skills used together with a result, and no required component is a gap or not assessed.
- **Partly evidenced:** some components evidenced but not together, or a required component is partial, a gap or not assessed.
- **Not yet evidenced:** no component has evidence.

Always show "k of n components backed by strong or relevant evidence".

---

## 5. Report

- One self-contained HTML file built from `assets/report_template.html`. Replace **only** the JSON in `<script id="report-data">`; the template draws every chart and table from it. Set `"illustrative": false`.
- Publish it as an HTML artifact or page; otherwise save `report_<report_id>.html` and send the file. Mention that "Save as PDF" in the report exports it.
- Write in plain language, in English or French as requested. Mark every implicit item "Inference". Show "Not assessed" in a neutral dashed style, never as the bottom of a scale. Present gaps as next steps.
- State in the report that it was generated with AI assistance and is guidance only.
- Layout, data fields and checks: `references/report.md`.

---

## 6. Privacy, GDPR and the EU AI Act

**Purpose limit.** The report supports the person's own preparation. Do not use this skill, or its output, to screen, rank, shortlist or evaluate candidates for an employer, or to decide admission, grades or educational level. The AI Act lists AI systems used for recruitment or selection (including analysing and filtering applications and evaluating candidates), and systems that determine admission or evaluate learning outcomes, as high-risk (Annex III, points 3 and 4) [S6, S18]. If an organisation wants such a use, stop and refer it to legal review.

**GDPR principles** [S5]
- **Lawful basis and transparency:** the person provides the data for this purpose and is told what is done with it. When an organisation (university, career service) runs the analysis, it obtains explicit consent and the person can withdraw it.
- **Minimisation:** use only what the analysis needs. Do not ask for or use age, date of birth, photo, nationality, family situation, health, religion, ethnicity, sexual orientation, political or union views. Ignore them if present in the CV and never infer them.
- **No discrimination:** no inference from protected characteristics, including age; career stage comes from experience only.
- **Storage limitation:** keep identifiable data only as long as needed; use a pseudonymous ID in reports.
- **Rights:** the person can correct their profile and challenge any conclusion.
- **Minors:** if the person states they are under 18, proceed only with information they choose to share, apply the student stage, and, where an organisation processes the data, follow its rules on parental consent.

**Human-centred skills.** Assess durable human skills only from behavioural examples (a situation, an action, a result), never from personality labels. Never assess wellbeing.

---

## 7. Worked example (illustrative)

The template ships with a fictional report: a student applying for a Data Analyst internship at a subscription company. Open `assets/report_template.html` to see the expected output.
