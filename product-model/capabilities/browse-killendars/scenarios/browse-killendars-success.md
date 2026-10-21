---
kind: primary
routes:
  main: Desktop
steps:
- text: Open the local calendar catalog.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Show each Killendar name, size, last change, password protection and active selection.
  kind: product
  entities:
  - entity: killendar
    effect: reads
    facts:
    - Name
    - File location
    - Size
    - Last changed
    - Password protection
    - Session access
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

# List the Killendars in the data folder

## Trigger

The User opens Manage Killendars.

## Outcome

Every Killendar in the data folder is listed with its name, size, when it last changed and whether it is encrypted, with the open one marked.
