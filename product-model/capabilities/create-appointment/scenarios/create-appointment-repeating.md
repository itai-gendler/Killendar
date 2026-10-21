---
kind: alternate
routes:
  main: Desktop
steps:
- text: Enter details, frequency, interval, weekly days if applicable, and an ending choice.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Save the repeating series with its initial empty skipped dates.
  kind: product
  entities:
  - entity: repeating-series
    effect: creates
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
  contexts:
    main:
      place: desktop::appointment
  actor: user
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
- kind: code
  role: implementation
  target: Services/CalendarCommands.cs
- kind: code
  role: implementation
  target: Killendar.Cli/Program.cs
---

# Create a repeating appointment

## Trigger

The User selects a supported repeat frequency while composing.

## Outcome

One repeating series is saved. The preview shows up to four dates found within three years using the same calendar expansion as the views.

## Edge cases

- A monthly date absent from a month is skipped; a yearly February 29 occurs in leap years.
- Weekly patterns with no selected weekdays use the weekday of the start.
- An unreadable or nonpositive interval defaults to one; a selected count or end-date limit must be readable.
