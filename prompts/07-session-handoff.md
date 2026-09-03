# Prompt 07 - Session Handoff

Prepare a handoff for the current task.

Requirements:
1. Check current Git status.
2. Summarize files changed in this session.
3. Summarize validation commands and results.
4. Summarize unfinished work, risks, and blockers.
5. Update the relevant Memory Bank files:
   - `memory-bank/activeContext.md`
   - `memory-bank/progress.md`
   - `memory-bank/module-<MODULE_NAME>-status.md`
   - If this is the orchestrator session, also update `memory-bank/orchestrator-status.md`
6. If there is cross-module impact, update or create `dev-doc/<CONTRACT>.md`.

Finish with a startup prompt that the next AI session can copy and run.
