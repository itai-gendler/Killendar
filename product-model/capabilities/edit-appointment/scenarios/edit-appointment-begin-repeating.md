---
kind: alternate
routes:
  main: Desktop
steps:
- text: Select a repeat pattern and save.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Replace the ordinary appointment with a repeating series.
  kind: product
  entities:
  - entity: appointment
    effect: removes
  - entity: repeating-series
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
    - Frequency
    - Interval
    - Weekdays
    - End condition
    - Skipped dates
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
---

# Give an ordinary appointment a repeat pattern

## Trigger

The User adds a repeat pattern to an existing ordinary entry.

## Outcome

The entry becomes a repeating series retaining its appointment details.
