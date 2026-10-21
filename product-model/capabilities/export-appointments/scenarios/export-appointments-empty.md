---
kind: edge
routes:
  main: Desktop
steps:
- text: Request an export from an empty calendar.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Report that there is nothing to export.
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

# Report an empty calendar

## Trigger

The User requests export with no saved entries.

## Outcome

The Product reports that there is nothing to export.
