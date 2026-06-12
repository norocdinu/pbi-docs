# pbi-docs — Power BI Documentation Plugin

A Claude Code plugin that documents Power BI reports using a generator + critic agent pair, grounded in the report's `.pbip` project files.

## What's inside

| Component | Name | Role |
|---|---|---|
| Agent | `handover-documenter` | Reads the .pbip (TMDL/PBIR or legacy); runs in recon mode (surfaces a Discovery Report of gaps + irrelevant-section candidates) or write mode (drafts the doc per the handbook template from the user's answers) |
| Agent | `handover-verifier` | Independent auditor: checks handbook compliance AND ground-truths claims against the .pbip files |
| Skill | `handover-docs` | The shared standard: handbook rules, template, quality checklist |
| Command | `/pbi-docs:document-report <path>` | Interview-first loop: recon → interview the user → confirm → draft → verify → refine until done |

## How the command works

The command is **interview-first** — it gathers context and confirms scope with you *before* writing, instead of producing a document full of TODOs. It (1) reads the report and surfaces what it can't determine, (2) asks you for the missing context and whether you have additional documents/Jira/exports, (3) confirms which irrelevant sections to omit, then (4) drafts, verifies, and (5) loops with you to resolve any remaining `⚠️ TODO` notes until you're happy.

## Usage

```
/pbi-docs:document-report ./Reports/MyReport.pbip
```

If your report is a `.pbix`, re-save it first: Power BI Desktop → File → Save As → "Power BI project files (.pbip)".

## The handbook standard

`skills/handover-docs/SKILL.md` and `template.md` encode the team's **Data Storytelling Handover Handbook** — its sections, rules, and quality checklist. Keep them in sync with the handbook as it evolves; the verifier audits every document against this standard.

## Install (team, via marketplace)

In any Claude Code session, run these two lines:

```
/plugin marketplace add norocdinu/pbi-docs
/plugin install pbi-docs@pbi-docs
```

That's it — the agents, skill, and `/pbi-docs:document-report` command are now available.

Prefer the terminal? The same thing without opening a session:

```bash
claude plugin marketplace add norocdinu/pbi-docs
claude plugin install pbi-docs@pbi-docs
```

## Update

When new changes have been pushed, update in any Claude Code session:

```
/plugin marketplace update pbi-docs
/plugin update pbi-docs@pbi-docs
```

1. `marketplace update` re-pulls the latest catalog from git.
2. `plugin update` installs the newest version of the plugin itself.

Or from the terminal, without opening a session:

```bash
claude plugin marketplace update pbi-docs
claude plugin update pbi-docs@pbi-docs
```

> **Note:** updates only appear if the `version` in `.claude-plugin/plugin.json` was bumped (see [Versioning](#versioning)). If `/plugin` reports you're already on the latest, the version wasn't changed.

## Local development / testing

```
claude --plugin-dir ./pbi-docs
```

After edits, run `/reload-plugins` to pick up changes without restarting. Validate with `claude plugin validate ./pbi-docs`.

## Versioning

Bump `version` in `.claude-plugin/plugin.json` when publishing changes — users only receive updates when the version changes.
