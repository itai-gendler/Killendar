---
kind: primary
routes:
  main: Desktop
steps:
- text: Change startup, close-to-tray or address-suggestion choices.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::about
  actor: user
- text: Save Preferences for startup checking, Windows startup, closing to the tray and address suggestions.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Startup update check
    - Start with Windows
    - Close to system tray
    - Address suggestions
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

# Change About settings

## Trigger

The User turns one of the About switches on or off: checking for updates on startup, starting with Windows, closing to the system tray, or address suggestions.

## Outcome

The choice is saved at once and applies from then on; nothing else needs saving.
