---
kind: primary
routes:
  main: Desktop
steps:
- text: Reload the active file from disk.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::calendar
  actor: user
- text: Reload the Killendar and its appointments, repeating series, single-date edits and categories.
  kind: product
  entities:
  - entity: killendar
    effect: changes
    facts:
    - Session access
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
    - Created
    - Modified
  - entity: repeating-series
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
    - Created
    - Modified
    - Frequency
    - Interval
    - Weekdays
    - End condition
    - Skipped dates
  - entity: single-date-edit
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
    - Created
    - Modified
    - Original occurrence
  - entity: category
    effect: reads
    facts:
    - Name
    - Color
  contexts:
    main:
      place: desktop::calendar
  actor: user
references:
- kind: code
  role: implementation
  target: Features/Security/SecurityController.cs
- kind: code
  role: implementation
  target: Services/EventStore.Encryption.cs
- kind: code
  role: implementation
  target: Services/EventStore.cs
---

# Reload the open Killendar

## Trigger

The open Killendar's file has changed outside the app, and the User reloads it.

## Outcome

The calendar shows the file's current appointments and categories. An encrypted Killendar already unlocked in this session reloads without asking for its password again.
