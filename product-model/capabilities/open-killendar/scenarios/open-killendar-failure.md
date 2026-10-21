---
kind: edge
routes:
  main: Desktop
steps:
- text: Open a file that cannot be loaded.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Report the open failure.
  kind: product
  entities: []
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
  target: Services/EventStore.cs
- kind: code
  role: implementation
  target: Services/EventStore.Schema.cs
---

# Report an open failure

## Trigger

The chosen file cannot be opened.

## Outcome

The Product reports the failure. During a catalog switch it attempts to return to the previous data folder and calendar.
