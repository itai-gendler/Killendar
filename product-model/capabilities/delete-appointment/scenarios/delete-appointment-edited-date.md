---
kind: alternate
routes:
  main: Desktop
steps:
- text: Open the single-date edit from the calendar, on the day it now shows.
  kind: actor
  entities:
  - entity: single-date-edit
    effect: reads
    facts:
    - Title
    - Start
    - End
  contexts:
    main:
      place: desktop::calendar
  actor: user
- text: Keep just this date, choose Delete and confirm.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Remove the single-date edit and add its original date to the repeating series' skipped dates.
  kind: product
  entities:
  - entity: single-date-edit
    effect: removes
  - entity: repeating-series
    effect: changes
    facts:
    - Skipped dates
    - Modified
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: The repeating series no longer generates that original date, so nothing from it shows there.
  kind: condition
  entities:
  - entity: repeating-series
    effect: reads
    facts:
    - Skipped dates
  contexts:
    main:
      place: desktop::calendar
references:
- kind: code
  role: implementation
  target: Features/Appointments/AppointmentEditor.cs
- kind: code
  role: implementation
  target: Services/EventStore.Persistence.cs
- kind: code
  role: implementation
  target: Shell/RepeatPanel.cs
---

# Delete a date that has its own single-date edit

## Trigger

The User deletes a date of a repeating series that already has its own single-date edit, possibly moved to another day.

## Outcome

The single-date edit is gone, and its original date is added to the series' skipped dates, so the series does not generate that date again. The rest of the series is unchanged.
