---
kind: alternate
routes:
  main: Desktop
steps:
- text: Move the individually edited entry.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::calendar
  actor: user
- text: Change the single-date edit start and end.
  kind: product
  entities:
  - entity: single-date-edit
    effect: changes
    facts:
    - Start
    - End
    - Modified
  contexts:
    main:
      place: desktop::calendar
  actor: user
references:
- kind: code
  role: implementation
  target: Features/Calendar/CalendarController.cs
- kind: code
  role: implementation
  target: Services/EventStore.Queries.cs
- kind: code
  role: implementation
  target: Services/Recurrence.cs
- kind: code
  role: implementation
  target: Views/TimeGridView.Interaction.cs
- kind: code
  role: implementation
  target: Views/MonthView.xaml.cs
- kind: code
  role: implementation
  target: Services/EventStore.Persistence.cs
---

# Move an existing single-date edit

## Trigger

The User moves an already replaced date.

## Outcome

The existing single-date edit is moved and retains its original occurrence.
