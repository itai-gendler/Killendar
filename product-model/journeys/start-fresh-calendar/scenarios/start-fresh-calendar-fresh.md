---
kind: primary
result: achieved
routes:
  main: Desktop
steps:
- text: Confirm starting fresh.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::password
  actor: user
  capability: start-new-killendar
- text: Preserve the old Killendar and open a new Killendar.
  kind: product
  entities:
  - entity: killendar
    effect: changes
    facts:
    - Name
    - File location
    - Session access
    - Active
    as: old
  - entity: killendar
    effect: creates
    facts:
    - Name
    - File location
    - Size
    - Last changed
    - Password protection
    - Session access
    - Active
    to: Plaintext
    as: new
  - entity: category
    effect: creates
    facts:
    - Name
    - Color
    with: new
  contexts:
    main:
      place: desktop::calendar
  actor: user
  capability: start-new-killendar
- text: Inspect the empty calendar.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::calendar
  actor: user
  capability: browse-calendar
- text: Show that no appointments are scheduled.
  kind: product
  entities:
  - entity: appointment
    effect: reads
    facts:
    - Title
    - Start
    - End
    - All day
    - Location
    - Description
    - Attendees
    - Categories
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

# Start fresh and reach the empty calendar

## Trigger

The User cannot unlock the active Killendar and chooses New Killendar at the unlock prompt.

## Outcome

The User is in the calendar of a new, empty Killendar, and the locked one is kept aside.
