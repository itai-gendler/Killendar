---
kind: alternate
routes:
  main: Desktop
steps:
- text: Choose a calendar already in the data folder.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Reuse the existing Killendar.
  kind: product
  entities:
  - entity: killendar
    effect: reads
    facts:
    - Name
    - File location
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

# Reuse a file already in the catalog

## Trigger

The chosen .kcal already resides in the configured data folder.

## Outcome

The existing file is selected without creating a duplicate.
