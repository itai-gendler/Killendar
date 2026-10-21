---
kind: alternate
routes:
  main: Command line
steps:
- text: Request the agenda from the active file or a specified existing absolute file path.
  kind: actor
  entities: []
  contexts:
    main:
      place: command-line
  actor: user
- text: Read appointment dates, repeating series dates and single-date edits for the requested range.
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
    - Categories
  - entity: repeating-series
    effect: reads
    facts:
    - Title
    - Start
    - End
    - All day
    - Location
    - Categories
  - entity: single-date-edit
    effect: reads
    facts:
    - Title
    - Start
    - End
    - All day
    - Location
    - Categories
  contexts:
    main:
      place: command-line
  actor: user
references:
- kind: code
  role: implementation
  target: Features/Calendar/CalendarController.cs
- kind: code
  role: implementation
  target: Services/EventStore.Queries.cs
- kind: code
  role: implementation
  target: Services/Recurrence.cs
- kind: code
  role: implementation
  target: Views/AgendaView.cs
- kind: code
  role: implementation
  target: Views/TimeGridViews.cs
- kind: code
  role: implementation
  target: Views/MonthView.xaml.cs
- kind: code
  role: implementation
  target: Shell/DayAgendaPanel.cs
- kind: code
  role: implementation
  target: Killendar.Cli/Program.cs
---

# Read a bounded agenda

## Trigger

The User requests a start date, one to 31 days and an optional result limit.

## Outcome

The command returns appointments overlapping the range, all-day entries first and then by start, with a default maximum of 50 or a requested maximum from one to 100.

## Edge cases

- The result includes identity and whether each entry is recurring.
- Agenda reading does not create files, migrate data or change the calendar.
