# Module-Level AI Rules

Copy this directory into any module that may be opened by AI tools independently.

Purpose:
- The module can still identify its responsibility boundary when opened or cloned alone.
- The module always reads and updates the root project's `memory-bank/` and `dev-doc/`.
- If the AI cannot locate the root project, it must ask the user for the root path. It must not create a second module-level `memory-bank/`.

After copying, replace:
- `<ROOT_PROJECT>`
- `<ROOT_PROJECT_PATH>`
- `<MODULE_NAME>`
- `<MODULE_PATH>`
- `<MODULE_DESCRIPTION>`
- `<MODULE_GIT_URL>`
- `<MODULE_BRANCH>`
- `<MODULE_STATUS_FILE>`

Keep these rules lightweight to avoid drift from the root rules.
