---
kind: alternate
routes:
  main: Desktop
steps:
- text: Choose whole-series scope on a generated date, then choose an assigned category as primary and
    save the edited entry.
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

# Make a category primary on a whole series

## Trigger

The User opens a date of a repeating series, chooses the whole series, chooses Make primary on one of its categories, and saves.

## Outcome

That category moves to the front of the series' categories, and every date the series generates takes its color.
