# Prompt 09 - Initialize Standalone Module AI Rules

Enable lightweight AI rules for a module that may be opened or cloned independently.

Module information:
- Root project name: `<ROOT_PROJECT>`
- Root project path: `<ROOT_PROJECT_PATH>`
- Module name: `<MODULE_NAME>`
- Module path: `<MODULE_PATH>`
- Module description: `<MODULE_DESCRIPTION>`
- Git URL: `<MODULE_GIT_URL>`
- Default branch: `<MODULE_BRANCH>`
- Dev command: `<MODULE_DEV_COMMAND>`
- Test command: `<MODULE_TEST_COMMAND>`
- Build command: `<MODULE_BUILD_COMMAND>`

First read:
- `ai-workspace-kit/templates/module-level/README.md`
- `ai-workspace-kit/templates/module-level/AGENTS.md`
- `ai-workspace-kit/templates/module-level/.cursor/rules/`
- `ai-workspace-kit/templates/module-level/.clinerules/`
- `ai-workspace-kit/templates/module-level/.codex/`
- `ai-workspace-kit/templates/module-level/.kiro/`

Create or update in `<MODULE_PATH>`:
- `AGENTS.md`
- `.cursor/rules/00-module-rules.mdc`
- `.cursor/rules/memory-bank-protocol.mdc`
- `.clinerules/README.md`
- `.clinerules/memory-bank-protocol.md`
- `.codex/README.md`
- `.kiro/README.md`
- `dev-doc/README.md`, only to point cross-module contracts back to root `dev-doc/`

Key rules:
1. If the module is opened as a submodule under the root project, read `../memory-bank/` and `../dev-doc/`.
2. If the module is an independent clone, read and update `<ROOT_PROJECT_PATH>/memory-bank/` and `<ROOT_PROJECT_PATH>/dev-doc/`.
3. Edit only this module by default.
4. Write cross-module contracts before implementation.
5. Do not create a second `memory-bank/` inside the module.
6. Do not overwrite important existing rules. Merge with existing files when they exist.

Finish with:
- Files created or updated.
- A standalone module startup prompt.
- The root Memory Bank update path.
