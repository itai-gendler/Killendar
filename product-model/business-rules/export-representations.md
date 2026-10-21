---
appliesTo:
- type: entity
  id: repeating-series
- type: entity
  id: single-date-edit
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
  target: Services/HtmlExport.cs
---

# ICS preserves patterns while CSV and HTML expand dates

ICS carries series rules and their exceptions. A range containing a generated date carries the whole selected series and every single-date edit. CSV and HTML contain expanded dates within a finite export span; endless patterns use a horizon one year from today for whole-calendar output.
