# Prompt 10 - Initialize AI Role Rules

Initialize AI role rules for the current complex project.

Roles:
- `@architect`: architect
- `@pm`: product manager
- `@dev`: developer
- `@algorithm`: algorithm engineer
- `@uiux`: UI/UX engineer
- `@agent`: agent engineer
- `@qa`: QA engineer

First read:
- `ai-workspace-kit/templates/roles/`
- `ai-workspace-kit/templates/cursor-rules/roles/`
- `ai-workspace-kit/templates/clinerules/roles/`

Create or update:
- `.ai-rules/roles/README.md`
- `.ai-rules/roles/architect.md`
- `.ai-rules/roles/pm.md`
- `.ai-rules/roles/dev.md`
- `.ai-rules/roles/algorithm.md`
- `.ai-rules/roles/uiux.md`
- `.ai-rules/roles/agent.md`
- `.ai-rules/roles/qa.md`
- `.cursor/rules/roles.mdc`
- `.clinerules/roles.md`

Requirements:
1. Add module paths relevant to each role based on the module list.
2. Keep root `memory-bank/` as the only source of project state.
3. Standalone module sessions must still write back to the root Memory Bank.
4. Do not overwrite important existing rules. Merge with existing role rules when present.
5. Finish with a role summary and usage examples.
