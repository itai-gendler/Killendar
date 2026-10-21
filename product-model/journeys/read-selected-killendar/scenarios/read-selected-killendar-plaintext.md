---
kind: primary
result: achieved
routes:
  main: Desktop
steps:
- text: Open the selected calendar.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
  capability: open-killendar
- text: Open the Killendar and carry the User to its calendar.
  kind: product
  entities:
  - entity: killendar
    effect: changes
    facts:
    - Session access
    - Active
  contexts:
    main:
      place: desktop::calendar
  actor: user
  capability: open-killendar
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

# Open a plaintext Killendar and read it

## Trigger

The User opens an existing plaintext file.

## Outcome

The selected calendar’s entries are visible.
