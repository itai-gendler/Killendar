---
kind: alternate
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
  - entity: single-date-edit
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

# Remove a category from a single-date edit

## Trigger

The User is editing a date that already has its own single-date edit, deselects one of its categories, and saves with just this date.

## Outcome

Only that single-date edit loses the category.
