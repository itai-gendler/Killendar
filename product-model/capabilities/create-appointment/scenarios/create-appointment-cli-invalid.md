---
kind: validation
routes:
  main: Command line
steps:
- text: Submit invalid creation input.
  kind: actor
  entities: []
  contexts:
    main:
      place: command-line
  actor: user
- text: Report the request validation error.
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

# Reject an invalid creation request

## Trigger

The command receives invalid or unsupported fields, invalid dates, or an empty title.

## Outcome

The command reports an error without saving an entry.
