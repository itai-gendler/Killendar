---
kind: primary
result: achieved
routes:
  main: Desktop
steps:
- text: Open the selected protected calendar.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
  capability: open-killendar
- text: Show the password process for the Killendar.
  kind: product
  entities:
  - entity: killendar
    effect: changes
    facts:
    - Session access
    - Active
  contexts:
    main:
      place: desktop::password
  actor: user
  capability: open-killendar
- text: Supply the password.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::password
  actor: user
  capability: unlock-killendar
- text: Open the Killendar and carry the User to its calendar.
  kind: product
  entities:
  - entity: killendar
    effect: changes
    facts:
    - Session access
  contexts:
    main:
      place: desktop::calendar
  actor: user
  capability: unlock-killendar
- text: Inspect the displayed period.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::calendar
  actor: user
  capability: browse-calendar
- text: Show appointments and repeating series dates.
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
  contexts:
    main:
      place: desktop::calendar
  actor: user
  capability: browse-calendar
references:
- kind: code
  role: implementation
  target: Features/Security/SecurityController.cs
- kind: code
  role: implementation
  target: Services/EventStore.Encryption.cs
- kind: code
  role: implementation
  target: Features/Calendar/CalendarController.cs
- kind: code
  role: implementation
  target: Services/EventStore.Queries.cs
- kind: code
  role: implementation
  target: Services/Recurrence.cs
---

# Unlock a protected Killendar and read it

## Trigger

The User opens a protected file.

## Outcome

After successful unlock its schedule is visible.
