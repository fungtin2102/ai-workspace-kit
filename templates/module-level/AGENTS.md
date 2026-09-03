# Codex Module Instructions - <MODULE_NAME>

This workspace is responsible for `<MODULE_NAME>`, namely `<MODULE_DESCRIPTION>`.

## Context Lookup

Prefer the parent root project, usually:
- `../`
- or user-provided `<ROOT_PROJECT_PATH>`

Required root context:
- `../AGENTS.md`
- `../.cursor/rules/`
- `../.clinerules/`
- `../.ai-rules/roles/`
- `../memory-bank/`
- `../dev-doc/`

If this module is an independent clone and those paths do not exist, ask the user for the root project path or ask them to open the root project as a workspace root. Do not create a second `memory-bank/` inside the module.

Local lightweight rules may be read from:
- `AGENTS.md`
- `.cursor/rules/`
- `.clinerules/`
- `.codex/`
- `.kiro/`

## Module Identity

- Root project: `<ROOT_PROJECT>`
- Root project path: `<ROOT_PROJECT_PATH>`
- Module name: `<MODULE_NAME>`
- Module path: `<MODULE_PATH>`
- Git URL: `<MODULE_GIT_URL>`
- Default branch: `<MODULE_BRANCH>`

## Responsibilities

- `<MODULE_RESPONSIBILITY_1>`
- `<MODULE_RESPONSIBILITY_2>`
- `<MODULE_RESPONSIBILITY_3>`

## Boundaries

- Edit only this module by default.
- Write cross-module API, field, event, database, or configuration changes to root `dev-doc/` first.
- Do not edit other modules unless explicitly requested and their paths are provided.
- Do not read excluded directories listed in root or module rules.

## Common Commands

```bash
<MODULE_DEV_COMMAND>
<MODULE_TEST_COMMAND>
<MODULE_BUILD_COMMAND>
```

## Required Status Update

Update:
- `../memory-bank/module-<MODULE_NAME>-status.md`

If `../memory-bank/` does not exist, use the user-provided root path:
- `<ROOT_PROJECT_PATH>/memory-bank/module-<MODULE_NAME>-status.md`

If the root Memory Bank cannot be located, stop and ask for the root project path.

Record:
- Completed work.
- Key files changed.
- Validation commands and results.
- Cross-module impact.
- Risks, blockers, and next steps.
