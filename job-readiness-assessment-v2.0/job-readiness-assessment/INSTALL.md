# Installation

How to load the **job-readiness-assessment** skill into an AI agent.

The skill is a folder. Keep this structure and this exact folder name:

```
job-readiness-assessment/
├── SKILL.md
├── references/
└── assets/
```

**If you downloaded this repository with GitHub's "Code → Download ZIP":** GitHub names the folder after the repository and branch (for example `job-readiness-assessment-main`). Unzip it, rename the folder to `job-readiness-assessment`, and re-zip it where a ZIP is needed. Claude rejects a skill whose folder name does not match the `name` in `SKILL.md`.

---

## 1. Claude app (web, desktop, mobile)

Available on Free, Pro, Max, Team and Enterprise plans.

1. **Turn on file creation.** Individual plans: **Settings → Capabilities → "Create and edit files"**. Team: on by default. Enterprise: an owner enables code execution and skills under **Organization settings → Plugins & skills**.
2. **Zip the folder** so the ZIP contains `job-readiness-assessment/` with `SKILL.md` inside it.
3. Go to **Customize → Skills**, click **+**, then **Create skill → Upload a skill**, and choose the ZIP.
4. **Toggle the skill on.**
5. **Use it.** Start a chat, paste a job posting (or link) and attach a CV. Claude loads the skill automatically.

If the upload fails, check the ZIP size, that the folder name matches the skill name, and that `SKILL.md` is inside the folder.

Official guide: [Use skills in Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude)

---

## 2. Claude Code

Copy the folder (no ZIP) to one of these locations:

| Scope | Location |
|---|---|
| All your projects | `~/.claude/skills/job-readiness-assessment/` |
| One project only | `.claude/skills/job-readiness-assessment/` inside the project |

For example, from a terminal:

```bash
git clone <this-repository-url> ~/.claude/skills/job-readiness-assessment
```

Claude Code detects the skill without a restart. If the `skills` folder did not exist when your session started, run `/reload-skills`.

**Use it** in either of two ways:
- Describe the task and Claude loads the skill automatically.
- Type `/job-readiness-assessment` to call it directly.

Official guide: [Extend Claude with skills](https://code.claude.com/docs/en/skills)

---

## 3. Claude API and Agent SDK

The folder follows the Agent Skills format. To use it in your own agent, see [Agent Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) and [Agent Skills in the SDK](https://docs.claude.com/en/docs/agent-sdk/skills). The agent needs file access to read `references/` and to write the HTML report.

---

## 4. Other AI agents and assistants

Agents that do not support the skills format can still follow the instructions.

1. **Instructions:** paste the content of `SKILL.md` into the agent's custom instructions, system prompt or project instructions. Leave out the block between the two `---` lines at the top.
2. **Knowledge files:** upload the files in `references/` and `assets/report_template.html` as project or knowledge files.
3. **File output:** the report is an HTML file. If the agent cannot create files, it uses the text fallback described in `references/report.md`.
4. **Use it:** share a job posting and a CV and ask for a readiness report.

Results depend on the agent's ability to read attached files, search the web for company facts and write files.

---

## Before you use it

- **Guidance only.** The skill helps the person applying. Do not use it to screen, rank or select candidates, or to decide admissions or grades. Under the EU AI Act these are high-risk uses (Annex III, points 3 and 4).
- **Share only what is needed.** A CV with work history and evidence is enough. Remove date of birth, photo, address, and ID or bank details first.
- **Organisations** running it for groups (universities, career services) should read `references/deployment.md` first. It covers consent, involving the data protection officer, and running a pilot.
- **Preview the output:** open `assets/report_template.html` in a browser to see a fictional example report.
