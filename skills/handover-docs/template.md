# Handover Documentation — Template

> Mirrors the **Data Storytelling Handover Handbook**. Gather context from the user
> *before* filling this in — don't write placeholders and then ask.
> Sections are a *baseline standard*: keep the structure for sections that apply.
> If a section genuinely does not apply to this report, **confirm with the user and
> omit it**, then record it under "Sections intentionally omitted" below — do not
> leave empty `N/A` stubs, and never omit a section without confirming first.
> Do **not** add sections or standards beyond this template. Where the handbook is
> silent, ask the user — do not assume. Only genuine unknowns the user could not
> answer remain as a clearly-labelled `⚠️ TODO — confirm with <role/owner>`.

---

# Handover Handbook — <Project / Report Name>

**Prepared by:** <name, role>  **Date:** <date>  **Outgoing owner:** <name>  **Incoming owner:** <name>

> **Sections intentionally omitted (confirmed with owner):** <list any baseline sections
> dropped because they don't apply to this report, each with a one-line reason — e.g.
> "3.3 Row-Level Security — no roles defined; single-user filter handled in Power Query".
> Remove this note if nothing was omitted.>

## Handover Log

Tracks each handover session held.

| # | Domain (Business/Technical) | Handover Item | Method (Virtual/F2F) | Date | Handover owner | Participants | Status | Confidence (1-5) | Resources |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | <Business/Technical> | <e.g. Process & KPIs> | <Virtual/F2F> | <date> | <name> | <names> | <Planned/Done> | <1-5> | <link> |

> Confidence level = the incoming owner's overall understanding of the topic discussed in that session (1 = none, 5 = full).

---

# Part A — Business Documentation

## 1. Business Context
High-level business context for the whole project: the business domain (e.g. Sales, Finance, Operations), the company strategy it supports, and background needed to interpret the data meaningfully.

<placeholder>

## 2. Business Glossary
Key business terms, definitions, and abbreviations used in the project, so terminology is interpreted consistently across stakeholders, consumers, and maintainers.

| Term / Abbreviation | Definition |
| --- | --- |
| <term> | <definition> |

## 3. Project Purpose & Objectives
The purpose of the report and the specific goals it achieves: the business problem addressed, the decisions it supports, and the expected outcomes.

<placeholder>

## 4. Audience and Use-Cases
Who consumes the report and in what context. Audience = the teams/departments accessing it (e.g. Senior Management, Sales Ops, Finance Controllers). Use-cases = concrete scenarios (e.g. monitoring monthly revenue targets, identifying underperforming regions).

| Audience | Use-case |
| --- | --- |
| <team> | <scenario> |

## 5. Stakeholders
Key stakeholders and their roles/responsibilities, including a RACI matrix.

| Stakeholder | Role | R | A | C | I |
| --- | --- | --- | --- | --- | --- |
| <name> | <role> | <✓> | <✓> | <✓> | <✓> |

## 6. Business Definitions and Metrics
The single source of truth for all business logic in the report. Define every KPI/metric, eliminating ambiguity (e.g. Revenue gross vs net; Active Customer = purchase within 30 vs 90 days).

| KPI / Metric | Definition (incl. ambiguities resolved) | Calculation formula | Data source | Business interpretation of ↑ / ↓ |
| --- | --- | --- | --- | --- |
| <metric> | <definition> | <formula> | <source> | <meaning> |

## 7. Process Diagram / Flow
End-to-end data journey: source systems → extraction/ingestion → transformation → storage → consumption. Note data dependencies, refresh schedules, and integration points (essential for troubleshooting).

<diagram / screenshot or description>

---

# Part B — Technical Documentation

## 1. General Information
**Report Name:** <value>
**Workspace URL:** <value>
**App URL:** <value>
**Business Owner:** <value>
**Product Owner:** <value>
**Refresh Schedule:** <value>

## 2. Data Sources
Where the data originates. (Credentials/auth inventory — mandatory.)

| Data source name | Connection details | Authentication Method | Gateway |
| --- | --- | --- | --- |
| <e.g. Snowflake> | <server / warehouse / db.schema> | <e.g. Password + MFA> | <Yes/No> |

### 2.1 Solution Architecture Overview
Overall architecture of the solution and how the layers are organized. For a two-layer architecture, explain each layer and its responsibility (e.g. Semantic Model holds connections/transformations/relationships/measures/business logic; Report File connects via live connection and handles visuals/navigation/filters/UX).

<placeholder>

### 2.2 Architectural Rationale
Reasoning behind the chosen architecture and its benefits (e.g. scalability, easier maintenance, centralized business logic, performance, reusable datasets, simpler version control, separation of modeling vs reporting).

<placeholder>

## 3. Data Model
Architecture of the semantic model: tables, relationships, security, and main transformations.

### 3.1 Tables overview
| Table Name | Table Type (Fact/Dim/Bridge) | Storage (Import/DQ/Dual) | Description / Key Columns (or ref to back-end docs) |
| --- | --- | --- | --- |
| <table> | <type> | <storage> | <description> |

### 3.2 Relationships overview
*Include a data model diagram/screenshot.*

| From Table | From Column | To Table | To Column | Relationship type | Comments |
| --- | --- | --- | --- | --- | --- |
| <table> | <col> | <table> | <col> | <e.g. One-to-many> | <comment> |

### 3.3 Row-Level Security overview
*If security is configured in the back end, link to the page where it is described.*

| Role Name | Table Filtered | DAX Filter Expression |
| --- | --- | --- |
| <role> | <table> | <expression> |

### 3.4 Data transformation
List any transformation happening in Power Query:
- Appends: <…>
- Merges: <…>
- Query folding (if applicable): <…>
- Custom M functions: <…>

## 4. Calculations (DAX)
Core business logic, complex DAX measures, and calculation groups.

| KPI Name | Measure name | KPI Definition | Measure definition (calculation) | Comment |
| --- | --- | --- | --- | --- |
| <KPI> | <[Measure]> | <definition> | <DAX> | <comment> |

## 5. Calculated Columns & Tables
Comprehensive list of any calculated columns or calculated tables, with details for each.

| Name | Type (Column/Table) | Host table | Definition | Purpose |
| --- | --- | --- | --- | --- |
| <name> | <type> | <table> | <DAX> | <why> |

## 6. Calculation Groups & Functions
Any Calculation Groups created via Tabular Editor, or functions used in the report.

<placeholder>

## 7. Report Overview

### 7.1 Pages overview
| Page name | Page description | Page-specific filters |
| --- | --- | --- |
| <page> | <description> | <filters> |

### 7.2 Filtering
| Filter Name | Filter table | Filter Column | Available to user (slicer) | All-pages filter | Page filter (if yes, list) |
| --- | --- | --- | --- | --- | --- |
| <filter> | <table> | <col> | <Yes/No> | <Yes/No> | <pages> |

### 7.3 Visuals overview
| Visual Name | Page name | Filter applied (if any) | Interaction exception | Comments |
| --- | --- | --- | --- | --- |
| <visual> | <page> | <filter> | <exception> | <comment> |

### 7.4 Bookmarks, buttons, custom visuals & access request flow
Bookmarks, buttons, custom visuals, and any other details. Include the access request flow and approvers. (Access inventory — mandatory.)

**Access request link:** <ServiceNow / form link>
**Access type:** <value>
**Approver(s):** <name(s)>

> If access is granted based on specific rules, list each approver.

## 8. Data Validation Approach
How data validation is handled in the solution. If validation/QA pages exist in the model or report, explain: where to find them, their purpose, who is expected to use them, and what reconciliation/validation checks are available.

<placeholder>

## 9. Incident Management
How incidents are raised, triaged, and resolved for this solution — open issues, known problems, escalation path, and support contacts.

<placeholder>
