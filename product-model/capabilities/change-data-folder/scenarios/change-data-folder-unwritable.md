---
kind: edge
routes:
  main: Desktop
steps:
- text: Choose an unwritable storage folder.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Report the folder problem.
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
  target: Services/EventStore.cs#SetDataDir
---

# Keep the current data folder

## Trigger

The selected folder cannot be created or written.

## Outcome

The Product reports failure and does not persist the new folder choice.
