---
kind: validation
routes:
  main: Desktop
steps:
- text: Submit an invalid or conflicting name.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Report the name problem.
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

# Reject a conflicting or invalid file name

## Trigger

The User enters an invalid file name or a name already present.

## Outcome

No rename occurs and the problem is reported. An omitted .kcal extension is appended; blank or unchanged names leave the file as it is.
