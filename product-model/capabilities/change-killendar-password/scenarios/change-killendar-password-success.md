---
kind: primary
routes:
  main: Desktop
steps:
- text: Enter and confirm a new nonempty password.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::password
  actor: user
- text: Replace the Killendar password and retain the open session.
  kind: product
  entities:
  - entity: killendar
    effect: changes
    facts:
    - Password protection
    - Session access
  contexts:
    main:
      place: desktop::password
  actor: user
references:
- kind: code
  role: implementation
  target: Features/Security/SecurityController.cs
- kind: code
  role: implementation
  target: Services/EventStore.Encryption.cs
---

# Change a Killendar's password

## Trigger

The open Killendar is encrypted; the User enters a new password twice and confirms.

## Outcome

The Killendar is now opened with the new password, and it stays open.
