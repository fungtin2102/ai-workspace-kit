# Prompt 03 - Start Module Work

You are now working in the `<MODULE_NAME>` module session.

Module information:
- Path: `<MODULE_PATH>`
- Responsibility: `<MODULE_DESCRIPTION>`
- Git URL: `<MODULE_GIT_URL>`
- Current task: `<TASK_DESCRIPTION>`

First read:
- Root `AGENTS.md`
- Module `AGENTS.md`
- `../memory-bank/projectbrief.md`
- `../memory-bank/productContext.md`
- `../memory-bank/systemPatterns.md`
- `../memory-bank/techContext.md`
- `../memory-bank/activeContext.md`
- `../memory-bank/progress.md`
- `../memory-bank/module-<MODULE_NAME>-status.md`
- Any relevant contract documents under `../dev-doc/`

If this module is an independent clone and the parent root project cannot be found, read local lightweight rules:
- `AGENTS.md`
- `.cursor/rules/`
- `.clinerules/`
- `.codex/`
- `.kiro/`

Then ask the user for `<ROOT_PROJECT_PATH>` and read:
- `<ROOT_PROJECT_PATH>/memory-bank/`
- `<ROOT_PROJECT_PATH>/dev-doc/`

Do not create or maintain a second `memory-bank/` inside this module.

Execution rules:
1. Edit only files inside `<MODULE_PATH>` by default.
2. If a cross-module change is needed, write the contract in root `dev-doc/` first and state which module must coordinate.
3. Follow the module's existing stack and coding style.
4. Run reasonable validation.
5. In root checkout, update `../memory-bank/module-<MODULE_NAME>-status.md`.
6. In standalone clone mode, update `<ROOT_PROJECT_PATH>/memory-bank/module-<MODULE_NAME>-status.md`.

Start the task unless there is not enough information to proceed safely.
