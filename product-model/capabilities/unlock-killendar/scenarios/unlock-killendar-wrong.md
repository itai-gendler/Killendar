---
kind: validation
routes:
  main: Desktop
steps:
- text: Submit an incorrect password.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::password
  actor: user
- text: Show the rejected-password message.
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
- kind: code
  role: implementation
  target: Services/EventStore.cs
---

# Retry a rejected password

## Trigger

The User supplies a password that cannot open the file.

## Outcome

The password process shows an error and asks again.
