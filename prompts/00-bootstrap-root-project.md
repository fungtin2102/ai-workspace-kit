# Prompt 00 - Bootstrap Root Project

Initialize an AI collaboration control layer for the current multi-module project.

Project information:
- Root project name: `<ROOT_PROJECT>`
- Project description: `<ROOT_PROJECT_DESCRIPTION>`
- Root Git URL: `<ROOT_GIT_URL>`
- Root branch: `<ROOT_BRANCH>`
- Default module branch: `<DEFAULT_MODULE_BRANCH>`

Modules:

| Module | Path | Git URL | Branch | Responsibility |
|--------|------|---------|--------|----------------|
| `<MODULE_A>` | `<MODULE_A_PATH>` | `<MODULE_A_GIT_URL>` | `<MODULE_A_BRANCH>` | `<MODULE_A_DESCRIPTION>` |
| `<MODULE_B>` | `<MODULE_B_PATH>` | `<MODULE_B_GIT_URL>` | `<MODULE_B_BRANCH>` | `<MODULE_B_DESCRIPTION>` |

Please do the following:
1. Create or update root `AGENTS.md` and define this workspace as the orchestrator session.
2. Create `.ai-control.yaml` to record root metadata, modules, tool entry points, excluded directories, and worktree conventions.
3. Create `.aiignore`, `.cursorignore`, and `.clineignore`.
4. Create base `.cursor/rules/` and `.clinerules/` rules.
5. Create `.ai-rules/roles/` for `@architect`, `@pm`, `@dev`, `@algorithm`, `@uiux`, `@agent`, and `@qa`.
6. Connect role rules through `.cursor/rules/roles.mdc` and `.clinerules/roles.md`.
7. Create the six root `memory-bank/` core files and `memory-bank/orchestrator-status.md`.
8. Create `dev-doc/README.md` and document the cross-module contract workflow.
9. Generate a `.gitmodules` draft or a list of `git submodule add` commands.
10. Do not read or reference deprecated history directories. If directories such as `archive/` or `legacy/` exist, add them to excluded rules.
11. Finish with files created or updated, missing information, and recommended next steps.

Use existing project files when they exist. If information is missing, use `TODO` placeholders. Do not invent facts.
