---
kind: alternate
routes:
  main: Desktop
steps:
- text: Choose whole-series scope on a generated date, then select a category and save the edited entry.
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

# Assign a category to a whole series

## Trigger

The User opens a date of a repeating series, chooses the whole series, selects a category and saves.

## Outcome

The category is added to the series, so every date it generates shows it; single-date edits keep their own assignments.
