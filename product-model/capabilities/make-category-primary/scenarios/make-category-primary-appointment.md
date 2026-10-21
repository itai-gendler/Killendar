---
kind: primary
routes:
  main: Desktop
steps:
- text: Choose an assigned category as primary and save the edited entry.
  kind: actor
  entities:
  - entity: category
    effect: reads
    facts:
    - Name
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Place the chosen name first in the saved category assignments.
  kind: product
  entities:
  - entity: appointment
    effect: changes
    facts:
    - Categories
    - Modified
  - entity: category
    effect: reads
    facts:
    - Name
  contexts:
    main:
      place: desktop::appointment
  actor: user
references:
- kind: code
  role: implementation
  target: Shell/Categories.cs
- kind: code
  role: implementation
  target: Services/EventStore.Categories.cs
- kind: code
  role: implementation
  target: Features/Appointments/AppointmentEditor.cs
---

# Make a category primary on an appointment

## Trigger

The User is editing an ordinary appointment, chooses Make primary on one of its categories, and saves.

## Outcome

That category moves to the front of the appointment's categories, so its color now paints the appointment.

## Edge cases

- Choosing an unassigned defined name as primary also adds it to the assignments.
