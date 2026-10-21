---
kind: alternate
routes:
  main: Desktop
steps:
- text: Enable starting with Windows.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::about
  actor: user
- text: Save and read back the Preferences Windows startup choice.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Start with Windows
  contexts:
    main:
      place: desktop::about
  actor: user
references:
- kind: code
  role: implementation
  target: Features/About/AboutController.cs
- kind: code
  role: implementation
  target: Services/StartupRegistration.cs
- kind: code
  role: implementation
  target: Shell/CloseToTray.cs
- kind: code
  role: implementation
  target: Shell/LocationLookup.cs
---

# Start minimized with Windows

## Trigger

The User enables starting with Windows.

## Outcome

The next Windows sign-in starts the application minimized. If the registration write is refused, the displayed choice reflects the actual registration.
