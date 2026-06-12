# pbi-docs — Power BI Documentation Plugin

A Claude Code plugin that documents Power BI reports using a generator + critic agent pair, grounded in the report's `.pbip` project files.

## What's inside

| Component | Name | Role |
|---|---|---|
| Agent | `handover-documenter` | Reads the .pbip (TMDL/PBIR or legacy), gathers business context, drafts the doc per the handbook template |
| Agent | `handover-verifier` | Independent auditor: checks handbook compliance AND ground-truths claims against the .pbip files |
| Skill | `handover-docs` | The shared standard: handbook rules, template, quality checklist |
| Command | `/pbi-docs:document-report <path>` | Runs the full documenter → verifier loop (max 2 fix rounds) |

## Usage

```
/pbi-docs:document-report ./Reports/MyReport.pbip
```

If your report is a `.pbix`, re-save it first: Power BI Desktop → File → Save As → "Power BI project files (.pbip)".

## ⚠️ Before first use

`skills/handover-docs/SKILL.md` and `template.md` contain `TODO` markers — they must be populated from the team's handover handbook. Until then, the verifier audits against a default checklist, not your official standard.

## Install

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

To update later, after new commits are pushed:

```
/plugin marketplace update pbi-docs
```

## Local development / testing

```
claude --plugin-dir ./pbi-docs
```

After edits, run `/reload-plugins` to pick up changes without restarting. Validate with `claude plugin validate ./pbi-docs`.

## Versioning

Bump `version` in `.claude-plugin/plugin.json` when publishing changes — users only receive updates when the version changes.
