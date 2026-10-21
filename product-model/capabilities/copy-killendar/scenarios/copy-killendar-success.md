---
kind: primary
routes:
  main: Desktop
steps:
- text: Copy the selected calendar file.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Put the Killendar file location on the clipboard as a file attachment.
  kind: product
  entities:
  - entity: killendar
    effect: reads
    facts:
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

# Copy a Killendar

## Trigger

The User selects a Killendar in Manage Killendars and copies it.

## Outcome

The .kcal file is on the clipboard as a file, ready to paste into a folder or attach to an email.
