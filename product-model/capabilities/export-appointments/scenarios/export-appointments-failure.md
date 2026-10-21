---
kind: edge
routes:
  main: Desktop
steps:
- text: Choose an unwritable export destination.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Report the write failure.
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
  target: Services/HtmlExport.cs
---

# Report a failed export

## Trigger

The selected destination cannot be written.

## Outcome

The Product reports export failure.
