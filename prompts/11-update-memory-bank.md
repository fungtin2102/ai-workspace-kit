# Prompt 11 - Update Memory Bank

Run `update memory bank` for this project.

Requirements:
1. Read the six root Memory Bank core files:
   - `projectbrief.md`
   - `productContext.md`
   - `systemPatterns.md`
   - `techContext.md`
   - `activeContext.md`
   - `progress.md`
2. Read the relevant module status file:
   - `memory-bank/module-<MODULE_NAME>-status.md`
3. If this is the orchestrator session, read:
   - `memory-bank/orchestrator-status.md`
   - `memory-bank/module-*-status.md`
4. Read recently relevant `dev-doc/` contract documents.
5. Update Memory Bank based on the actual current state.

Prioritize updates to:
- `memory-bank/activeContext.md`
- `memory-bank/progress.md`
- `memory-bank/module-<MODULE_NAME>-status.md`
- `memory-bank/orchestrator-status.md` for the orchestrator session

Rules:
- Mark unknown information as `TODO`.
- Do not invent completion status.
- If validation was not run, write `not run`; do not write that it passed.
- Modules must not maintain a second `memory-bank/`; all status is written to the root project.

Finish with:
- Files updated.
- Current focus.
- Next steps.
- Risks or blockers.
