---
kind: primary
routes:
  main: Desktop
steps:
- text: Choose a view, previous or next period, today, or a day to inspect.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::calendar
  actor: user
- text: Read the overlapping appointments, generated repeating series dates and single-date edits.
  kind: product
  entities:
  - entity: appointment
    effect: reads
    facts: &id001
    - Title
    - Start
    - End
    - All day
    - Location
    - Description
    - Attendees
    - Categories
  - entity: repeating-series
    effect: reads
    facts: *id001
  - entity: single-date-edit
    effect: reads
    facts: *id001
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
  target: Views/AgendaView.cs
- kind: code
  role: implementation
  target: Views/TimeGridViews.cs
- kind: code
  role: implementation
  target: Views/MonthView.xaml.cs
- kind: code
  role: implementation
  target: Shell/DayAgendaPanel.cs
- kind: code
  role: implementation
  target: Killendar.Cli/Program.cs
---

# Read a period and selected day

## Trigger

The User selects a view and calendar period.

## Outcome

The requested appointments are shown. Selecting a day or appointment opens that day’s agenda; editing is an explicit next action.

## Edge cases

- An empty range shows an empty calendar or agenda.
- Week pages by seven days, Day by one day, and Agenda by one month across a 60-day window.
- Agenda groups by starting date; an appointment beginning before the window appears under the first visible date.
- All-day entries precede timed entries. Overlapping timed appointments remain individually readable.
