---
kind: primary
result: achieved
routes:
  main: Desktop
steps:
- text: Accept adding the external file.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
  capability: load-killendar
- text: Create a local Killendar copy and continue opening it.
  kind: product
  entities:
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
  - entity: appointment
    effect: creates
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
    with: killendar
  - entity: repeating-series
    effect: creates
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
    with: killendar
  - entity: single-date-edit
    effect: creates
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
    with: killendar
  - entity: category
    effect: creates
    facts:
    - Name
    - Color
    with: killendar
  contexts:
    main:
      place: desktop::killendars
  actor: user
  capability: load-killendar
- text: Open the copied Killendar for the User.
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
- text: Inspect the copied schedule.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::calendar
  actor: user
  capability: browse-calendar
- text: Show its appointments.
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
  target: Controls/KillendarsDialog.xaml.cs
- kind: code
  role: implementation
  target: Services/EventStore.Catalog.cs
- kind: code
  role: implementation
  target: Features/Security/SecurityController.cs
---

# Open a copied plaintext Killendar from Windows

## Trigger

The User opens an external plaintext .kcal through Windows.

## Outcome

The local copy opens with the source preserved.
