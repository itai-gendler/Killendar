---
kind: primary
routes:
  main: Desktop
steps:
- text: Open the selected calendar.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Open the Killendar and select it as active.
  kind: product
  entities:
  - entity: killendar
    effect: changes
    facts:
    - Session access
    - Active
  contexts:
    main:
      place: desktop::calendar
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
  target: Services/EventStore.cs
- kind: code
  role: implementation
  target: Services/EventStore.Schema.cs
---

# Open an existing plaintext calendar

## Trigger

The User opens an existing calendar without password protection.

## Outcome

Its appointments and category definitions become the active calendar. A draft is closed when switching to a different file; merely inspecting the catalog preserves it.
