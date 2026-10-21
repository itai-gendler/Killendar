---
kind: alternate
routes:
  main: Desktop
steps:
- text: Choose whole-series scope on a generated date, then deselect an assigned category and save the
    edited entry.
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
  - entity: repeating-series
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

# Remove a category from a whole series

## Trigger

The User opens a date of a repeating series, chooses the whole series, deselects one of its categories, and saves.

## Outcome

The series and every date it generates no longer carry that category.
