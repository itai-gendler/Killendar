---
kind: edge
routes:
  main: Command line
steps:
- text: Request creation while the desktop calendar is unavailable.
  kind: actor
  entities: []
  contexts:
    main:
      place: command-line
  actor: user
- text: Report that the calendar is not ready for the command.
  kind: product
  entities: []
  contexts:
    main:
      place: command-line
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

# Report an unavailable command target

## Trigger

The User invokes creation while the desktop application is absent, opening, or has no open calendar.

## Outcome

The command reports failure and creates no entry.
