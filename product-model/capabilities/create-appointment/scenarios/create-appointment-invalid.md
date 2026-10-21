---
kind: validation
routes:
  main: Desktop
steps:
- text: Save incomplete or invalid input.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Show the validation error and retain the input.
  kind: product
  entities: []
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

# Keep invalid input in the editor

## Trigger

The User saves a blank title, unreadable date or time, non-increasing timed span, or incomplete repeat ending.

## Outcome

No appointment is saved. The editor remains open with an error at the offending input.
