---
kind: edge
routes:
  main: Desktop
steps:
- text: Cancel the password process.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::password
  actor: user
- text: End this unlock attempt.
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

# Cancel unlocking

## Trigger

The User cancels the password process.

## Outcome

On launch the application exits. During a calendar switch the application attempts to reopen the previous calendar instead.
