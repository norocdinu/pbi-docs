---
name: handover-docs
description: Use when someone is leaving a project or role and needs to document their work, or when asked to "write documentation", "handover document", "handover doc", "knowledge transfer doc", "transition documentation", "offboarding docs", or to capture a Power BI / data-reporting solution for the next owner. Produces a structured handover document following the Data Storytelling Handover Handbook.
---

# Handover Documentation

## Overview
Produce a handover document for a project, report, or role using the **Data Storytelling Handover Handbook** structure. The handbook is the single source of truth. The structure is a baseline standard — adapt per project, but **never invent sections or standards beyond the handbook, and where the handbook is silent, ask the user instead of assuming.**

**Interview first, write second.** Gather context and confirm scope with the user *before* drafting. Do not produce a document full of placeholders and then ask. If a section looks irrelevant to this report, confirm with the user and **omit** it rather than leaving an empty stub. Only genuine, unavoidable unknowns — things the user themselves could not provide — remain as a few clearly-labelled `⚠️ TODO` notes.

`template.md` (in this skill folder) mirrors the handbook's required sections with placeholder guidance. Use it as the skeleton for every handover doc.

## When to Use
- Someone is offboarding from / transitioning out of a project or role.
- Request to write handover / knowledge-transfer / transition / offboarding documentation.
- Documenting a Power BI or data-reporting solution for the next owner.

## Workflow

1. **Read `template.md`** in this skill folder — it defines the exact structure to follow.

2. **Gather context.** Establish what's being handed over and collect what the user already has. Determine scope:
   - **Business documentation**, **Technical documentation**, or **both**?
   - For a Power BI / report handover, both parts usually apply.

3. **Ask for missing mandatory content — do not assume.** The handbook treats these as required; if any is unknown, ask targeted questions:
   - **Credentials / data sources**: every data source, connection details, authentication method, gateway (Yes/No).
   - **Access request flow**: request link (ServiceNow/form), access type, approver(s).
   - **Contacts**: Business Owner, Product Owner, and the Stakeholders/RACI matrix.
   - **General info**: Report Name, Workspace URL, App URL, Refresh Schedule.
   - **Runbooks**: Data Validation Approach and Incident Management (open issues, escalation, support contacts).
   - **Handover log**: sessions held — domain, item, method, date, owner, participants, status, confidence (1-5).

   Batch related questions. Only ask about sections in scope. Don't block the whole doc on one missing answer — fill what you can, mark unknowns clearly (see step 5).

4. **Generate the document** following `template.md`:
   - Keep the handbook's section order and headings for sections that apply.
   - Match the handbook tone: professional and descriptive; open each section with a short purpose statement; put structured facts in the handbook's tables.
   - **Omit** sections the user confirmed are irrelevant to this report, and record each under a short "Sections intentionally omitted (confirmed with owner)" note near the top — so the baseline structure is still traceable without carrying empty stubs. Never omit a section without confirming first.
   - Never add sections, KPIs, standards, or conventions the handbook doesn't define.

5. **Handle gaps honestly.** Resolve everything you can during the interview. For the few facts the user genuinely could not provide, insert a clearly labelled `⚠️ TODO — confirm with <role/owner>` placeholder. Keep these minimal — a TODO is for an unavoidable unknown, never for something the report files actually answer. Do not fabricate values (credentials, owners, formulas, refresh schedules).

6. **Run the Quality Checklist** below before delivering.

7. **Deliver** as a `.md` file by default. Offer other formats (e.g. `.docx`, PDF) if the user prefers.

## Quality Checklist
Verify before delivering:

- [ ] Structure matches `template.md` / the handbook — section order and headings preserved for sections that apply.
- [ ] Scope (Business / Technical / both) agreed with the user and covered.
- [ ] Context gathered via interview *before* drafting; additional documents/Jira/context requested from the user.
- [ ] Irrelevant sections omitted only after user confirmation, and listed under "Sections intentionally omitted".
- [ ] Handover Log table present with at least one session row.
- [ ] **Credentials/auth inventory** complete: each data source has connection details, authentication method, and gateway.
- [ ] **Access request flow** captured: link, access type, approver(s).
- [ ] **Contacts** captured: Business Owner, Product Owner, Stakeholders/RACI.
- [ ] **General Information** filled: Report Name, Workspace URL, App URL, Refresh Schedule.
- [ ] Business Definitions & Metrics give definition + formula + source + interpretation per KPI.
- [ ] Data Model covered: tables, relationships (with diagram), RLS, transformations.
- [ ] **Runbooks** present: Data Validation Approach and Incident Management (incl. open issues / escalation).
- [ ] No invented sections, standards, or values beyond the handbook.
- [ ] Remaining gaps are few, each marked `⚠️ TODO` — nothing fabricated, no TODO hiding a file-derivable fact.
- [ ] Sections that don't apply are either omitted-with-confirmation (and listed) — not silently dropped, and not left as empty stubs.
- [ ] Delivered in the user's preferred format (`.md` default).

## Common Mistakes
- **Writing before interviewing** — producing a draft full of placeholders and *then* asking. Gather context and confirm scope first; the user should answer questions before the document is written, not after.
- **Assuming there's no other context** — not asking whether the user has additional documents, Jira tickets, or exports. Always ask.
- **Inventing structure** — adding sections/standards the handbook doesn't define. Don't. Ask the user instead.
- **Assuming silent details** — guessing credentials, owners, schedules, or formulas. Mark `⚠️ TODO` and ask.
- **Carrying dead sections** — leaving empty "N/A" stubs for parts that don't apply. Confirm with the user and omit them, recording the omission.
- **Omitting without asking** — dropping a section on your own judgement. Always confirm first.
- **Skipping the mandatory inventory** — access/credentials, contacts, and runbooks are required where they apply; don't drop them silently.
