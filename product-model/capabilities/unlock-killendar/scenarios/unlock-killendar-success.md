---
kind: primary
routes:
  main: Desktop
steps:
- text: Enter the file password and choose Unlock.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::password
  actor: user
- text: Open the Killendar after its password is accepted.
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
  target: Features/Security/SecurityController.cs
- kind: code
  role: implementation
  target: Services/EventStore.Encryption.cs
- kind: code
  role: implementation
  target: Services/EventStore.cs
---

# Unlock a protected calendar

## Trigger

The password process is shown for the selected file.

## Outcome

The Killendar opens and its calendar becomes available. Reloading it later in the same session does not ask for the password again.
