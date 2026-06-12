---
description: Document a Power BI report end-to-end using the documenter + verifier loop. Invoke with the path to the .pbip project folder, e.g. /pbi-docs:document-report ./Reports/TSA2025.pbip
disable-model-invocation: true
---

Document the Power BI report at: $ARGUMENTS

Workflow:
1. Run the **handover-documenter** subagent on the report. Pass it the .pbip path above and any context files or Jira references I've mentioned in this conversation. If the path points at a .pbix file, relay the documenter's request that I re-save it as a PBIP project before continuing.
2. When the draft is ready, run the **handover-verifier** subagent, passing it: the document path AND the same .pbip path. Do not pass it the documenter's reasoning or this conversation — only the document, the handover-docs skill, and the report files.
3. If the verdict is FAIL, send the verifier's full report back to **handover-documenter** to fix the blockers, then re-run the verifier.
4. Maximum 2 fix rounds. After that, show me the document plus any unresolved findings and let me decide.
5. On PASS, show me the final document and the verifier's grounding summary.
