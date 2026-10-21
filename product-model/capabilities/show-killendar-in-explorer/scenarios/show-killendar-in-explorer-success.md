---
kind: primary
routes:
  main: Desktop
steps:
- text: Request the selected file or data folder in Explorer.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Open Explorer at the Killendar file location or Preferences data folder.
  kind: product
  entities:
  - entity: killendar
    effect: reads
    facts:
    - File location
  - entity: preferences
    effect: reads
    facts:
    - Data folder
  contexts:
    main:
      place: desktop::killendars
  actor: user
references:
- kind: code
  role: implementation
  target: Controls/KillendarsDialog.xaml.cs
- kind: code
  role: implementation
  target: Services/EventStore.Catalog.cs
- kind: code
  role: implementation
  target: Features/Security/SecurityController.cs
---

# Show a Killendar in Explorer

## Trigger

The User asks Manage Killendars to show the selected Killendar, or the data folder, in Explorer.

## Outcome

Windows Explorer opens at the data folder, with the selected .kcal highlighted when there is one.
