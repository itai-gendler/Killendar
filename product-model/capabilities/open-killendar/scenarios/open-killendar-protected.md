---
kind: alternate
routes:
  main: Desktop
steps:
- text: Open the selected protected calendar.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Set the Killendar session access to awaiting unlock and show the password process.
  kind: product
  entities:
  - entity: killendar
    effect: changes
    facts:
    - Session access
    - Active
  contexts:
    main:
      place: desktop::password
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

# Continue opening at the password prompt

## Trigger

The selected calendar is password protected and has no usable session password.

## Outcome

The User reaches the password process for this calendar.
