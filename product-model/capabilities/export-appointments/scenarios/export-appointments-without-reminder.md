---
kind: alternate
routes:
  main: Desktop
steps:
- text: Choose scope, format and output destination.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Read Preferences and the Killendar protection to determine that no reminder is required.
  kind: product
  entities:
  - entity: preferences
    effect: reads
    facts:
    - Export reminder
  - entity: killendar
    effect: reads
    facts:
    - Password protection
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Read appointments, repeating series and single-date edits and write the chosen export.
  kind: product
  entities:
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

# Export without the reminder interaction

## Trigger

The User begins an export whose reminder is not applicable.

## Outcome

The selected calendar representation is written at the chosen destination.
