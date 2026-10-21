---
kind: alternate
routes:
  main: Command line
steps:
- text: Supply the title, local start and end, and optional all-day and other supported details.
  kind: actor
  entities: []
  contexts:
    main:
      place: command-line
  actor: user
- text: Save the appointment with no attendees and return its identity.
  kind: product
  entities:
  - entity: appointment
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

# Create through the command line

## Trigger

The User submits a supported creation request while the desktop calendar is open.

## Outcome

A single appointment is saved in the active calendar and its identity and dates are returned. All-day command-line input uses an exclusive end date.

## Edge cases

- The command accepts neither recurrence nor attendees.
- The title is required and limited to 200 characters; location and categories to 500 each, and description to 4000.
- Timed dates accept local ISO date-time to minutes or seconds; all-day dates use ISO dates.
