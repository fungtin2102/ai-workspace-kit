# Prompt 06 - Write A Cross-Module Contract First

Write the contract document for the following cross-module change before editing implementation code.

Change request:
- Requirement: `<CHANGE_REQUEST>`
- Affected modules: `<MODULE_A>`, `<MODULE_B>`, `<MODULE_C>`
- Contract path: `dev-doc/<CONTRACT_NAME>.md`

Document:
1. Background and goal.
2. Affected modules and responsibility boundaries.
3. API, event, database, configuration, or file-format changes.
4. Field tables, state machines, error codes, or event payloads.
5. Backward compatibility strategy.
6. Integration order.
7. Test checklist.
8. Implementation tasks for each module session.

After writing the contract, update:
- `memory-bank/activeContext.md`
- `memory-bank/module-<MODULE_NAME>-status.md` for affected modules

Finish with ready-to-use prompts for each module session.
