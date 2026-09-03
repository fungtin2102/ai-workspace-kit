# Prompt 01 - Initialize Memory Bank

Inspect the current project's root `memory-bank/`.

Requirements:
1. Create the directory if it does not exist.
2. Create any missing core files:
   - `projectbrief.md`
   - `productContext.md`
   - `systemPatterns.md`
   - `techContext.md`
   - `activeContext.md`
   - `progress.md`
3. Create `module-<MODULE_NAME>-status.md` for every module.
4. Create or update `memory-bank/orchestrator-status.md`.
5. Populate the files from the following project information:

Root project:
- Name: `<ROOT_PROJECT>`
- Description: `<ROOT_PROJECT_DESCRIPTION>`

Modules:
- `<MODULE_NAME>`: path `<MODULE_PATH>`, Git `<MODULE_GIT_URL>`, branch `<MODULE_BRANCH>`, responsibility `<MODULE_DESCRIPTION>`

Output rules:
- Use English.
- Use `TODO` for unknown information.
- Write project facts that help the next AI session continue work.
- Report which files were created or updated.
