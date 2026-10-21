---
kind: edge
routes:
  main: Command line
steps:
- text: Request an agenda from a file that cannot be read.
  kind: actor
  entities: []
  contexts:
    main:
      place: command-line
  actor: user
- text: Report the file-read failure.
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

# Report an unavailable agenda file

## Trigger

The requested file is missing, unreadable, or password protected.

## Outcome

The command reports that it cannot read the agenda; the command-line agenda does not prompt to unlock files.
