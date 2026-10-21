---
kind: alternate
routes:
  main: Desktop
steps:
- text: Choose an external .kcal file to load, or confirm adding one opened from Windows.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Copy the Killendar and its appointments, repeating series, single-date edits and categories into
    the data folder.
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
    to: Encrypted
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

# Load an encrypted Killendar

## Trigger

The User selects an external .kcal file.

## Outcome

A copy is added to the catalog with its contents and protection preserved; the source is unchanged. Manage Killendars selects the new row; a shell-open request continues to opening it.

## Edge cases

- A name collision appends a numeric suffix.
- The catalog Load action adds the file without immediately switching the active calendar.
