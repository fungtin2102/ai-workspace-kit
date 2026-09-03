# Migration Checklist

## Before Initialization

- [ ] Confirm the root project name.
- [ ] Confirm each module name, path, Git URL, and default branch.
- [ ] Confirm which directories AI tools must not read.
- [ ] Confirm each module's responsibility boundary.
- [ ] Confirm the formal documentation directory and the cross-module contract directory.

## Root Files

- [ ] Create root `AGENTS.md`.
- [ ] Create `.cursor/rules/`.
- [ ] Create `.clinerules/`.
- [ ] Create `.ai-rules/roles/`.
- [ ] Create `.cursor/rules/roles.mdc`.
- [ ] Create `.clinerules/roles.md`.
- [ ] Create root `memory-bank/` core files.
- [ ] Create `memory-bank/orchestrator-status.md`.
- [ ] Create `memory-bank/module-<MODULE_NAME>-status.md` for every module.
- [ ] Create `dev-doc/README.md`.
- [ ] Create `.gitmodules` or run `git submodule add`.
- [ ] Create `.ai-control.yaml`.
- [ ] Create `.aiignore`, `.cursorignore`, and `.clineignore`.

## Modules

- [ ] Every module has its own `AGENTS.md`.
- [ ] Modules opened independently have lightweight `.cursor/rules/`.
- [ ] Modules opened independently have lightweight `.clinerules/`.
- [ ] Modules opened independently have lightweight `.codex/`.
- [ ] Modules opened independently have lightweight `.kiro/`.
- [ ] Standalone module rules document the root project path or root lookup method.
- [ ] Modules do not maintain a second `memory-bank/`.
- [ ] Module status still goes to root `memory-bank/module-<MODULE_NAME>-status.md`.
- [ ] Every module documents responsibilities and non-responsibilities.
- [ ] Every module documents dev, test, and build commands.
- [ ] If the root Memory Bank cannot be found, the module AI asks for the root path instead of creating local memory.

## Worktrees

- [ ] Agree on the worktree base directory.
- [ ] Agree on branch naming conventions.
- [ ] Use one worktree per task.
- [ ] Remove completed worktrees and temporary branches after merge.

## AI Usage

- [ ] Orchestrator sessions start from the root project.
- [ ] Module sessions start from the module directory.
- [ ] Role triggers are available: `@architect`, `@pm`, `@dev`, `@algorithm`, `@uiux`, `@agent`, `@qa`.
- [ ] Long tasks start by reading the Memory Bank.
- [ ] Cross-module changes are documented in `dev-doc/` first.
- [ ] Each substantive session updates Memory Bank.
- [ ] New sessions use `prompts/12-follow-custom-instructions.md` to recover context.
- [ ] Milestones or context switches use `prompts/11-update-memory-bank.md`.
