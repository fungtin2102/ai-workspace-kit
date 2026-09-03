# Prompt 05 - Create A Git Worktree For A Parallel Task

Create an isolated Git worktree for this task.

Task information:
- Root project: `<ROOT_PROJECT>`
- Module: `<MODULE_NAME>`
- Module path: `<MODULE_PATH>`
- Base branch: `<BASE_BRANCH>`
- New task branch: `codex/<TASK_SLUG>`
- Worktree directory: `../worktrees/<ROOT_PROJECT>-<MODULE_NAME>-<TASK_SLUG>`
- Task description: `<TASK_DESCRIPTION>`

Please do the following:
1. Check Git status in `<MODULE_PATH>` and detect uncommitted changes.
2. Run or provide:
   `git worktree add ../worktrees/<ROOT_PROJECT>-<MODULE_NAME>-<TASK_SLUG> -b codex/<TASK_SLUG> origin/<BASE_BRANCH>`
3. In the new worktree, read module `AGENTS.md` and the root Memory Bank.
4. Start the task or output a startup prompt for a new AI session.
5. Record the worktree and task branch in `memory-bank/module-<MODULE_NAME>-status.md`.

If the module has uncommitted changes, do not overwrite them. Explain the risk and provide a safe path.
