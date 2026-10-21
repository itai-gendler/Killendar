---
kind: validation
routes:
  main: Desktop
steps:
- text: Choose a CSV with unsupported headers.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Report the required columns.
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

# Refuse unrecognized CSV headers

## Trigger

A chosen CSV lacks Subject or Start Date.

## Outcome

The entire CSV is refused with a message identifying the required columns; no rows are added.
