---
kind: alternate
routes:
  main: Desktop
steps:
- text: Choose whole-calendar scope for expanded output.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Read repeating series, appointments and single-date edits within the export span.
  kind: product
  entities:
  - entity: repeating-series
    effect: reads
    facts:
    - Title
    - Start
    - End
    - All day
    - Location
    - Description
    - Attendees
    - Categories
    - Created
    - Modified
    - Frequency
    - Interval
    - Weekdays
    - End condition
    - Skipped dates
  - entity: appointment
    effect: reads
    facts:
    - Title
    - Start
    - End
    - All day
    - Location
    - Description
    - Attendees
    - Categories
    - Created
    - Modified
  - entity: single-date-edit
    effect: reads
    facts:
    - Title
    - Start
    - End
    - All day
    - Location
    - Description
    - Attendees
    - Categories
    - Created
    - Modified
    - Original occurrence
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

# Bound a whole-calendar expanded export

## Trigger

The User exports the whole calendar to CSV or HTML with a series that never ends.

## Outcome

Expanded output uses a finite span including the calendar’s dated entries and a one-year-from-today horizon for endless series.
