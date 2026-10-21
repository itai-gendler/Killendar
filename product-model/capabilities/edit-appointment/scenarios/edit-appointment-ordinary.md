---
kind: primary
routes:
  main: Desktop
steps:
- text: Change the details and save.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Save the appointment details and modification time.
  kind: product
  entities:
  - entity: appointment
    effect: changes
    facts:
    - Title
    - Start
    - End
    - All day
    - Location
    - Description
    - Attendees
    - Categories
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
---

# Edit a single appointment

## Trigger

The User chooses Edit on an existing entry.

## Outcome

The saved appointment has the new details. Moving its readable start in the editor shifts the end by the same amount to preserve duration.

## Edge cases

- Cancel discards the editor copy.
- The desktop validation for new appointments also applies to edits.
- All-day editing shows the last covered date, so saving it repeatedly does not extend the span.
