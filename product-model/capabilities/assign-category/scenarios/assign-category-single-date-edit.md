---
kind: alternate
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

# Assign a category to a single-date edit

## Trigger

The User is editing a date that already has its own single-date edit, selects a category and saves with just this date.

## Outcome

Only that single-date edit gains the category; the rest of the series is unchanged.
