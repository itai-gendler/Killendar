---
kind: edge
routes:
  main: Desktop
steps:
- text: Choose a saved email without calendar content.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Report that no invitation was found.
  kind: product
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
references:
- kind: code
  role: implementation
  target: Features/Calendar/IcsTransfer.cs
- kind: code
  role: implementation
  target: Services/IcsService.cs
- kind: code
  role: implementation
  target: Services/CsvService.cs
- kind: code
  role: implementation
  target: Services/EmlService.cs
- kind: code
  role: implementation
  target: Services/EventStore.Categories.cs
- kind: code
  role: implementation
  target: Shell/SecurityHost.cs
---

# Report an email without an invitation

## Trigger

The chosen EML has no extractable calendar body.

## Outcome

The Product reports that there is no invitation and adds nothing.
