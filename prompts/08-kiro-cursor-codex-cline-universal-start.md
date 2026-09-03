# Prompt 08 - Universal Startup Prompt For Kiro / Cursor / Codex / Cline

You are entering a complex multi-module project.

Follow these rules:
1. First read root `AGENTS.md`.
2. Read rules under `.cursor/rules/` and `.clinerules/`.
3. If `.ai-rules/roles/` exists, read the role rules. When the user specifies `@pm`, `@dev`, `@algorithm`, `@uiux`, `@qa`, `@architect`, or `@agent`, follow that role.
4. Read the six root Memory Bank core files:
   - `projectbrief.md`
   - `productContext.md`
   - `systemPatterns.md`
   - `techContext.md`
   - `activeContext.md`
   - `progress.md`
5. If working inside a module, also read that module's `AGENTS.md` and root `memory-bank/module-<MODULE_NAME>-status.md`.
6. If this is a standalone module clone and the parent root is not available, read the module-level `.cursor/rules/`, `.clinerules/`, `.codex/`, and `.kiro/`, then ask the user for the root project path and read the root `memory-bank/` and `dev-doc/`.
7. Edit only within the module's responsibility boundary by default.
8. Write cross-module changes to root `dev-doc/` first.
9. Update the root Memory Bank after substantive work.

Important: keep `memory-bank/` root-only. Do not create a second `memory-bank/` inside modules.

Current task:

```text
<TASK_DESCRIPTION>
```

Briefly state the key context you loaded, then proceed. If information is missing, ask the minimum necessary questions.
