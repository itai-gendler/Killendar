---
appliesTo:
- type: capability
  id: create-appointment
  contexts:
  - place: command-line
references:
- kind: code
  role: implementation
  target: Services/CalendarCommands.cs
- kind: code
  role: implementation
  target: Services/CalendarCommandPipe.cs
---

# Command-line creation saves into the Killendar open on the desktop

The command hands the appointment to the running desktop application, which saves it in its active Killendar. The desktop must be running with that Killendar open and, when protected, unlocked; otherwise nothing is created.
