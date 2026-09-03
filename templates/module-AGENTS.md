# Codex Module Instructions - <MODULE_NAME>

This workspace is responsible for `<MODULE_PATH>`, namely `<MODULE_DESCRIPTION>`.

Read and follow first:
- `../.cursor/rules/`
- `../.clinerules/`
- `../.ai-rules/roles/`
- `../memory-bank/`
- `../dev-doc/`

If this module is opened as an independent clone and the parent paths do not exist, ask the user for the root project path or ask them to add the root project to the workspace. Keep `memory-bank/` root-only. Do not create a second Memory Bank inside this module.

## Responsibilities

- `<MODULE_RESPONSIBILITY_1>`
- `<MODULE_RESPONSIBILITY_2>`
- `<MODULE_RESPONSIBILITY_3>`

## Boundaries

- Do not edit other modules by default unless the user explicitly asks for it.
- Write cross-module contract changes to the root `dev-doc/` first.
- If another module must coordinate, update the relevant root `memory-bank/module-<OTHER_MODULE>-status.md` or report it to the orchestrator session.
- Do not read excluded directories, generated artifacts, or deprecated implementations listed in the root `AGENTS.md`.

## Common Commands

```bash
<MODULE_DEV_COMMAND>
<MODULE_TEST_COMMAND>
<MODULE_BUILD_COMMAND>
```

## Required Status Update

Update:
- `../memory-bank/module-<MODULE_NAME>-status.md`

If `../memory-bank/` does not exist, locate the root project first and update:
- `<ROOT_PROJECT_PATH>/memory-bank/module-<MODULE_NAME>-status.md`

Record:
- What was completed.
- Key files changed.
- Validation commands and results.
- Remaining blockers, risks, or next steps.
