---
kind: primary
routes:
  main: Desktop
steps:
- text: Enter and confirm a password for the open calendar.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::password
  actor: user
- text: Change the Killendar from plaintext to encrypted and keep it open.
  kind: product
  entities:
  - entity: killendar
    effect: changes
    facts:
    - Password protection
    - Session access
    from: Plaintext
    to: Encrypted
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

# Encrypt a Killendar

## Trigger

The open Killendar has no password; the User enters a password twice and confirms.

## Outcome

The Killendar is encrypted at rest and stays open. From now on it asks for this password when it is opened.
