---
kind: primary
routes:
  main: Desktop
steps:
- text: Enter a new calendar file name.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Rename the Killendar and retain the active selection at its new file location.
  kind: product
  entities:
  - entity: killendar
    effect: changes
    facts:
    - Name
    - File location
    - Active
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

# Rename a Killendar

## Trigger

The User renames a Killendar in Manage Killendars.

## Outcome

The file has the new name, with .kcal added when left out. If it was the active Killendar, it stays active under the new name.
