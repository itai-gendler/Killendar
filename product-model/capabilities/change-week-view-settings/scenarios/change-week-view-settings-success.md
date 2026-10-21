---
kind: primary
routes:
  main: Desktop
steps:
- text: Choose five or seven displayed days.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::calendar
  actor: user
- text: Save the Preferences work week choice and refresh Week view.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Work week
  contexts:
    main:
      place: desktop::calendar
  actor: user
references:
- kind: code
  role: implementation
  target: Shell/WorkWeek.cs
- kind: code
  role: implementation
  target: Views/TimeGridViews.cs
---

# Switch the work week on or off

## Trigger

The User switches Week view between a five-day work week and the full week.

## Outcome

The choice is saved. With the work week on, Week shows Monday through Friday whatever the first day of the week is.
