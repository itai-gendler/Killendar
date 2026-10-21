---
kind: primary
routes:
  main: Desktop
steps:
- text: Choose a writable folder or the executable folder.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Save the Preferences data folder and select its Default calendar for reopening.
  kind: product
  entities:
  - entity: preferences
    effect: changes
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
- kind: code
  role: implementation
  target: Services/EventStore.cs#SetDataDir
---

# Change the data folder

## Trigger

In Manage Killendars, the User picks another writable folder, or the folder beside Killendar.exe for a portable copy.

## Outcome

The catalog now lists that folder's Killendars and Default there becomes the active one. Killendars in the previous folder stay where they are.
