---
kind: primary
routes:
  main: Desktop
steps:
- text: Select a category and save the edited entry.
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
- text: Append the selected name to the saved category assignments.
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

# Assign a category to an appointment

## Trigger

The User is editing an ordinary appointment, selects a category that is not yet assigned, and saves.

## Outcome

The category is added after any already assigned. The first assigned category stays primary and keeps coloring the appointment.
