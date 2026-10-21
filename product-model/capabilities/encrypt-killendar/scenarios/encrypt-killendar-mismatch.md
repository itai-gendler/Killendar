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

# Reject mismatched passwords when encrypting

## Trigger

The entered password and confirmation differ.

## Outcome

The Killendar stays without a password and the mismatch is reported.
