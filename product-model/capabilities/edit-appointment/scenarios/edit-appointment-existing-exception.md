---
kind: alternate
routes:
  main: Desktop
steps:
- text: Keep just-this-date scope and save revised details.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Change the single-date edit while retaining its original occurrence and creation time.
  kind: product
  entities:
  - entity: single-date-edit
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

# Edit an existing single-date replacement

## Trigger

The chosen date already has a saved replacement.

## Outcome

The single-date edit is changed in place; another replacement is not added.
