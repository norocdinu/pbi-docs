---
name: handover-docs
description: Rules, template, and quality checklist for Power BI report handover documentation. Use when creating, revising, or verifying handover/knowledge-transfer documentation for a Power BI report. Loaded by the handover-documenter and handover-verifier agents as their source of truth.
---

# Handover Documentation Standard

<!-- TODO: This skill must be populated from the team's handover handbook.
     Run the skill-creation prompt against the handbook and replace every
     TODO block below. Neither agent should be used in production until
     the TODOs are resolved. -->

## Purpose

Defines what a valid handover document for a Power BI report looks like. The documenter agent writes to this standard; the verifier agent audits against it. Where this document is silent, agents must ask the user — never assume.

## Required structure

The document must follow `template.md` in this skill folder, with every mandatory section present and in order.

<!-- TODO: List the mandatory sections from the handbook, marking any
     optional ones explicitly. -->

## Style and tone rules

<!-- TODO: Extract from the handbook: language (EN/RO?), tense, heading
     conventions, how DAX/M code is presented (the agents default to
     verbatim fenced code blocks), table vs prose preferences. -->

## Content rules

- Every technical claim about the report must be traceable to the .pbip files.
- DAX and M code is quoted verbatim, never paraphrased.
- Credentials, tokens, and keys are never reproduced; reference their storage location instead.
- Unknowns are surfaced as questions to the user, not filled with plausible guesses.

<!-- TODO: Add handbook-specific content rules (e.g., required naming
     conventions, mandatory metadata header, classification labels). -->

## Quality checklist

The verifier audits each item; the documenter self-checks before handoff.

1. All mandatory template sections present, in order, correctly titled.
2. No unresolved markers: `[TO CONFIRM]`, `TODO`, `TBD`, placeholders.
3. Data sources documented with type and location, matching the M expressions.
4. All measures documented with home table and verbatim DAX.
5. All report pages documented; page list matches the report definition.
6. Refresh schedule, gateway, and workspace/deployment details stated.
7. Owners, stakeholders, and support contacts named.
8. Known issues and open tickets listed with IDs.
9. No secrets reproduced in the document.
10. Successor test: a competent Power BI developer with zero context could take over using this document alone.

<!-- TODO: Replace/extend with the handbook's own checklist items. -->
