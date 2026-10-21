---
kind: primary
routes:
  main: Desktop
steps:
- text: Select a calendar density level.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::calendar
  actor: user
- text: Save the Preferences calendar density and refresh the calendar.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Calendar density
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
  target: Views/CalendarChrome.cs
---

# Change calendar density

## Trigger

The User steps the calendar density up or down.

## Outcome

The density is saved. Week and Day redraw with hour, half-hour, twenty-minute or quarter-hour lines, and Month shows more or less detail per appointment.
