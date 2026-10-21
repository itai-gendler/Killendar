---
kind: validation
routes:
  main: Desktop
steps:
- text: Submit mismatched password entries.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::password
  actor: user
- text: Report the mismatch.
  kind: product
  entities: []
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

# Reject mismatched entries when removing the password

## Trigger

One password box is empty and the other is not, or the two entries differ.

## Outcome

The existing password stays and the mismatch is reported.
