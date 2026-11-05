# Report

Load at workflow step 8.

## 1. Layout: dashboard first, details below

The reader should grasp the result in under a minute.

| Order | Block | Content |
|---|---|---|
| 1 | Header | Role, employer, location, contract, career stage, person ID, date checked, report version; "Save as PDF" |
| 2 | At a glance | Four counts (requirements analysed; strong or relevant; to develop; not assessed), 2–3 sentence summary, limits |
| 3 | By requirement type | Stacked bars: status counts for required, preferred, contextual |
| 4 | Evidence strength | Stacked bar: assessed requirements by V0–V3 |
| 5 | Competencies | One card per competency: status, "k of n", skill chips, evidence, Inference or Stated |
| 6 | Skill by skill | Target (diamond) vs current (dot); not assessed shown at the edge, never as zero |
| 7 | Durable human skills | Layer D tiles with evidence label (D3, D14 excluded) |
| 8 | Top 3 priorities | Why, next step, hours |
| 9 | Plan | Weekly timeline |
| 10 | Full report (expandable) | Company; requirements; evidence vs role; plan; CV and interview preparation; sources, assumptions, limits |

## 2. Data block fields

| Key | Content |
|---|---|
| `illustrative` | `false` for real reports |
| `meta` | report_id, version, date_checked, person_id (pseudonymous), career_stage, job_title, employer, location, contract, source, language |
| `summary` | readiness (2–3 plain sentences), limitations |
| `company[]` | element, statement, type (`fact` / `analysis`), source |
| `competencies[]` | id, name, origin (`explicit` / `implicit`), rule, status (`demonstrated` / `partial` / `not_evidenced`), context, components (skill IDs) |
| `skills[]` | id, name, layer, requirement, origin, rule, target (1–4), current (0–4 or `null`), match (`strong` / `relevant` / `partial` / `gap` / `not_assessed`), label, verification, evidence, source, confidence, why, action — in priority order |
| `layer_d[]` | id, name, label |
| `priorities[]` | skill, why, action, hours (top 3) |
| `plan[]` | task, skill, start (week), weeks, deliverable, criterion |
| `interview` | positioning[], behavioural[], topics[], questions[] |
| `sources[]` | id, title, url, publisher, retrieved |
| `assumptions[]` | strings |

`current: 0` only with the person's own statement.

## 3. Writing and design rules

- Plain language; explain terms on first use.
- No percentage, gauge or overall score.
- "Not assessed" and "Not evidenced" are neutral and dashed, never the bottom of a scale.
- Every implicit item carries the "Inference" tag.
- Every status is also written as text, not shown by colour alone.
- Variable text in chips, badges and labels wraps inside its card (no `white-space: nowrap`).
- Gaps are written as next steps; "Not evidenced" is an evidence goal.
- CV advice never suggests claiming an unearned skill. No invented interview stages.
- Any practice case uses public or synthetic data.

## 4. Check after rendering

No script error; every chart visible; no chip or label overflows at about 1400 px and 390 px width; tile counts match the tables.

## 5. Fallback

Only if no HTML can be produced: say why, then give the four counts, the competency table (name, status, k of n), the skill table, the top 3 priorities and the plan as a numbered list.
