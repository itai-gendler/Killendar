---
kind: primary
routes:
  main: Desktop
steps:
- text: Move the selected entry to a date or time slot.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::calendar
  actor: user
- text: Save the appointment at the new start and end.
  kind: product
  entities:
  - entity: appointment
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

# Move an ordinary appointment

## Trigger

The User moves a saved entry to a destination in Month, Week or Day.

## Outcome

The appointment keeps its duration. Month retains the clock time; Week and Day moves use half-hour precision at hour or half-hour density, then twenty-minute or quarter-hour precision at finer density. All-day entries retain their covered day count.
