---
kind: edge
routes:
  main: Desktop
steps:
- text: Choose a file that cannot be copied.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Report the copy failure.
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
---

# Report a failed file load

## Trigger

The source is missing or copying fails.

## Outcome

The Product reports failure; a file-adoption attempt restores the previous open selection when necessary.
