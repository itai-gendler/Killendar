---
kind: edge
routes:
  main: Desktop
steps:
- text: Choose a source that cannot be imported.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Report the import failure.
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

# Report an import failure

## Trigger

Reading, parsing or persisting the selected file fails.

## Outcome

The Product reports import failure. An unsupported named time zone fails the import rather than guessing a local date.
