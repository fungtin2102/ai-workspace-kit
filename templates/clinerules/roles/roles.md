# AI Role Rules

In a target project, role definitions should live in:

```text
.ai-rules/roles/
```

Supported roles:
- `@architect`
- `@pm`
- `@dev`
- `@algorithm`
- `@uiux`
- `@agent`
- `@qa`

When the user specifies a role, follow that role's responsibilities. If no role is specified, choose the role that best matches the task.

All roles must follow these rules:
- Root `memory-bank/` is the single source of truth for project state.
- Module sessions stay inside their responsibility boundary by default.
- Cross-module contracts are written to root `dev-doc/` first.
- Meaningful work updates root `memory-bank/`.
