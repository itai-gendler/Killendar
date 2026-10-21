---
kind: edge
routes:
  main: Desktop
steps:
- text: Apply the password choice.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::password
  actor: user
- text: Report the password operation failure.
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

# Report a failed encryption

## Trigger

The calendar cannot be rewritten or replaced.

## Outcome

The Product reports that the password operation failed. When replacement fails, the original file is reopened with its existing password.
