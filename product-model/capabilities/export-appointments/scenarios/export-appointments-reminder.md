---
kind: alternate
routes:
  main: Desktop
steps:
- text: Choose an export scope and accept the reminder, optionally suppressing future reminders.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Read the Killendar protection and save the Preferences export reminder choice.
  kind: product
  entities:
  - entity: killendar
    effect: reads
    facts:
    - Password protection
  - entity: preferences
    effect: changes
    facts:
    - Export reminder
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Choose the output format and destination.
  kind: actor
  entities: []
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

# Export after the reminder interaction

## Trigger

The User begins an export from a protected calendar with reminders enabled.

## Outcome

After confirmation and choosing a destination, the selected calendar representation is written. Suppression is remembered if the reminder was accepted with that choice.

## Edge cases

- Canceling the reminder writes no output and does not remember suppression.
- The exchange output uses the chosen standard unencrypted format.
