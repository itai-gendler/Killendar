---
kind: primary
routes:
  main: Desktop
steps:
- text: Choose calendar month or rolling weeks and the visible span.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::calendar
  actor: user
- text: Save the Preferences month mode and visible weeks.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Month mode
    - Visible weeks
  contexts:
    main:
      place: desktop::calendar
  actor: user
references:
- kind: code
  role: implementation
  target: Views/MonthView.xaml.cs
- kind: code
  role: implementation
  target: Features/Calendar/CalendarController.cs
---

# Change Month view settings

## Trigger

The User switches Month between the calendar month and rolling weeks, or changes how many weeks it shows.

## Outcome

The mode and a span of one to six weeks are saved, and Month redraws with them.
