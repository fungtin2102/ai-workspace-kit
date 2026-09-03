# Prompt 02 - Add Or Verify Git Submodules

Use the following list to add or verify Git submodules for the current root project.

Module list:

```text
<MODULE_NAME_1>|<MODULE_PATH_1>|<MODULE_GIT_URL_1>|<MODULE_BRANCH_1>
<MODULE_NAME_2>|<MODULE_PATH_2>|<MODULE_GIT_URL_2>|<MODULE_BRANCH_2>
```

Please do the following:
1. Check whether `.gitmodules` already contains these modules.
2. For missing modules, generate or run:
   `git submodule add -b <MODULE_BRANCH> <MODULE_GIT_URL> <MODULE_PATH>`
3. Generate or run:
   `git submodule update --init --recursive`
4. Create `<MODULE_PATH>/AGENTS.md` for each module and document responsibility, boundaries, common commands, and status file.
5. If a module may be opened or cloned independently, initialize lightweight module-level rules from `ai-workspace-kit/templates/module-level/`:
   - `<MODULE_PATH>/AGENTS.md`
   - `<MODULE_PATH>/.cursor/rules/`
   - `<MODULE_PATH>/.clinerules/`
   - `<MODULE_PATH>/.codex/`
   - `<MODULE_PATH>/.kiro/`
   - `<MODULE_PATH>/dev-doc/README.md`, only to point back to the root `dev-doc/`
6. Update the module list in `memory-bank/projectbrief.md` and `memory-bank/orchestrator-status.md`.
7. Do not overwrite uncommitted changes inside any module.

Finish with:
- Which submodules were added.
- Which submodules already existed.
- Which modules received standalone-session lightweight rules.
- Confirmation that no module-level `memory-bank/` was created.
- Any Git URLs or branches that still need confirmation.
- Files recommended for commit.
