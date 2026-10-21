---
kind: validation
routes:
  main: Desktop
steps:
- text: Submit an invalid date range.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Report the invalid range.
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

# Correct an invalid export range

## Trigger

The User enters unreadable dates or an end before the start.

## Outcome

The range remains open for correction and no file is written.
