---
kind: validation
routes:
  main: Command line
steps:
- text: Request an agenda with invalid bounds.
  kind: actor
  entities: []
  contexts:
    main:
      place: command-line
  actor: user
- text: Report invalid usage.
  kind: product
  entities: []
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

# Reject invalid agenda bounds

## Trigger

The User requests an invalid start date, day count, result limit or path option.

## Outcome

The command reports invalid usage without reading an agenda.
