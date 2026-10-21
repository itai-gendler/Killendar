---
kind: edge
routes:
  main: Desktop
steps:
- text: Save the entered details.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Report the persistence failure and reload saved appointment data.
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
    - Description
    - Attendees
    - Categories
    - Created
    - Modified
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

# Keep the editor open after a write failure

## Trigger

A new entry cannot be saved to disk.

## Outcome

An error is shown and the editor remains open. The displayed calendar is reloaded from persisted data.
