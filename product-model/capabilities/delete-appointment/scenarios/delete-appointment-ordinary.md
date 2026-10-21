---
kind: primary
routes:
  main: Desktop
steps:
- text: Confirm deletion of the selected entry.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Remove the appointment.
  kind: product
  entities:
  - entity: appointment
    effect: removes
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

# Delete an ordinary appointment

## Trigger

The User is editing an appointment that does not repeat, chooses Delete and confirms.

## Outcome

The appointment is removed.

## Edge cases

- Canceling confirmation preserves the saved entry.
- A persistence failure is reported and the calendar reloads saved data.
