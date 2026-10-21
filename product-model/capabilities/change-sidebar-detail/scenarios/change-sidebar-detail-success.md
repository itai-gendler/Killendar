---
kind: primary
routes:
  main: Desktop
steps:
- text: Choose the detail level for the day agenda.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::calendar
  actor: user
- text: Save the Preferences sidebar detail and refresh the selected day.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Sidebar detail
  contexts:
    main:
      place: desktop::calendar
  actor: user
references:
- kind: code
  role: implementation
  target: Shell/Density.cs
- kind: code
  role: implementation
  target: Shell/DayAgendaPanel.cs
---

# Change sidebar detail

## Trigger

The User picks how much detail the selected day's agenda shows.

## Outcome

The level is saved independently of calendar density, and the day agenda redraws with it.
