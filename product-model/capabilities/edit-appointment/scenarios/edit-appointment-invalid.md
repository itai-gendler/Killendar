---
kind: validation
routes:
  main: Desktop
steps:
- text: Save an invalid edit.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Display an input error and retain the edit for correction.
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
---

# Correct invalid edited details

## Trigger

The User saves an invalid title, date, timed span or repeat ending.

## Outcome

The editor reports the invalid input and keeps the saved entry unchanged.
