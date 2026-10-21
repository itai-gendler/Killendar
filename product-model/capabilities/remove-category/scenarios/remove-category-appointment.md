---
kind: primary
routes:
  main: Desktop
steps:
- text: Deselect an assigned category and save the edited entry.
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
- text: Remove the selected name from the saved category assignments.
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

# Remove a category from an appointment

## Trigger

The User is editing an ordinary appointment, deselects one of its categories, and saves.

## Outcome

The appointment no longer carries that category; the category definition itself stays in the Killendar.
