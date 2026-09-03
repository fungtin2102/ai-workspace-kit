# Prompt 12 - Follow Custom Instructions / Recover Context

Follow the current project's custom instructions and recover context before continuing work.

First read:
- `AGENTS.md`
- `.cursor/rules/`
- `.clinerules/`
- `.ai-rules/roles/`
- `memory-bank/projectbrief.md`
- `memory-bank/productContext.md`
- `memory-bank/systemPatterns.md`
- `memory-bank/techContext.md`
- `memory-bank/activeContext.md`
- `memory-bank/progress.md`

If currently inside a module:
- Read that module's `AGENTS.md`.
- Read root `memory-bank/module-<MODULE_NAME>-status.md`.
- If the root `memory-bank/` cannot be found, ask for the root project path. Do not create a module-level `memory-bank/`.

Then output:
1. The project and module you detected.
2. Current focus and next steps.
3. Relevant risks.
4. How you will continue the current task.

Current task:

```text
<TASK_DESCRIPTION>
```
