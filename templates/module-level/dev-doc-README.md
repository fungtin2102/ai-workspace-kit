# Module Dev Doc - <MODULE_NAME>

This module should not maintain independent cross-module contract documents for the long term. Cross-module contracts should be written to the root `dev-doc/`.

Preferred location:
- `../dev-doc/`

If this module is an independent clone and the default path does not exist, ask the user for the root project path:
- `<ROOT_PROJECT_PATH>/dev-doc/`

Do not maintain a long-lived second contract directory inside this module.
