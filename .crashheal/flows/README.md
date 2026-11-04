# Maestro flows

Flows here can be listed in `reach.setupFlows` (run before every repro) or used by the agent as building blocks.
Use `${TEST_USER}` / `${TEST_PASSWORD}` placeholders; real values come from `reach.env` at run time.

Example `login.yaml`:

```yaml
appId: ${APP_ID}
---
- launchApp:
    clearState: true
- tapOn: "Sign in"
- tapOn:
    id: "email"
- inputText: ${TEST_USER}
- tapOn:
    id: "password"
- inputText: ${TEST_PASSWORD}
- tapOn: "Continue"
- assertVisible: "Home"
```
