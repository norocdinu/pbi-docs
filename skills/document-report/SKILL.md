---
description: Document a Power BI report end-to-end using an interview-first documenter + verifier loop. Invoke with the path to the .pbip project folder, e.g. /pbi-docs:document-report ./Reports/TSA2025.pbip
disable-model-invocation: true
---

Document the Power BI report at: $ARGUMENTS

This command is **interview-first**. YOU (the orchestrating session) are the only one who can talk to the user — the subagents run autonomously and cannot ask anything. So you must gather context and get confirmation from the user **before** any full draft is written. Never skip straight to a document full of TODO placeholders.

## Step 1 — Discovery (recon only, no draft)

Run the **handover-documenter** subagent in **RECON MODE**. Pass it the .pbip path above plus any context files / Jira references already mentioned in this conversation. Tell it explicitly: *"Recon mode: read the report and return a Discovery Report only. Do NOT write the handover document yet."*

- If the path points at a `.pbix` file, relay the documenter's request to re-save it as a PBIP project and stop until the user provides the `.pbip`.

The Discovery Report it returns has three parts: (a) what can be established from the files, (b) genuine gaps that need the user, (c) template sections that look **irrelevant to this report** (candidates to omit, with reasons).

## Step 2 — Interview the user (in this session)

Using the interactive question UI, grouped by topic, ask the user — and wait for answers:

1. **First, always:** "Do you have any additional documents, Jira tickets, source exports, or context I should use?" If they share anything, read it before continuing.
2. **The gaps** from the Discovery Report — business purpose & audience, owners/stakeholders, refresh schedule, gateway, workspace/app, access request flow & approvers, known issues. Batch into a few grouped questions; do not drip-feed. Let the user answer "don't know / skip" for any of them.
3. **Confirm the omissions:** for each section the recon flagged as irrelevant, confirm whether to **omit it entirely** or keep it. Do not omit anything the user hasn't confirmed.

## Step 3 — Confirm, then draft

Summarise back what you captured and which sections will be omitted. Get the user's explicit go-ahead. **Only then** run **handover-documenter** in **WRITE MODE**, passing it: the .pbip path, the user's answers, any context docs, and the confirmed list of sections to omit. It drafts the document — omitting the confirmed sections (recorded in a short "Sections intentionally omitted" note, not stubbed as N/A), and leaving only genuine, unavoidable unknowns as a few clearly-labelled `⚠️ TODO` notes.

## Step 4 — Verify

Run the **handover-verifier** subagent, passing it: the document path, the .pbip path, AND the confirmed list of intentionally-omitted sections (so it does not flag them as missing). Do not pass it the documenter's reasoning or this conversation — only the document, the handover-docs skill, the report files, and the omit list.

- If the verdict is FAIL, send the verifier's full report back to **handover-documenter** to fix the blockers, then re-run the verifier. Maximum 2 fix rounds. After that, show the user the document plus any unresolved findings and let them decide.

## Step 5 — Refine loop (until the user is done)

Show the user the document and point explicitly at the remaining `⚠️ TODO` notes. Ask: *"Do you have input to resolve any of these, or other changes you'd like? Or are you happy to finish here?"*

- If they provide input or changes → run **handover-documenter** in revision mode to improve the document, re-run the verifier if any technical claim changed, save, and **repeat this step**.
- If they confirm they're done → show the final document and the verifier's grounding summary, and stop.

The document file is saved after every step, so the user always has a usable document even mid-loop.
