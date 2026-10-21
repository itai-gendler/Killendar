---
kind: primary
routes:
  main: Desktop
steps:
- text: Apply matching empty password entries.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::password
  actor: user
- text: Change the Killendar from encrypted to plaintext and keep it open.
  kind: product
  entities:
  - entity: killendar
    effect: changes
    facts:
    - Password protection
    - Session access
    from: Encrypted
    to: Plaintext
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

# Remove a Killendar's password

## Trigger

The open Killendar is encrypted; the User leaves both password boxes empty and confirms.

## Outcome

The Killendar is written back as a plain SQLite file without a password, and it stays open.
