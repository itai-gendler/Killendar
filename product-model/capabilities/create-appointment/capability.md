---
availability:
- place: desktop
- place: command-line
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

# Create appointment

Save a new timed or all-day appointment. The desktop also creates repeating series; the command line creates a single appointment in the open desktop calendar.
