---
kind: alternate
routes:
  main: Desktop
steps:
- text: Choose an Outlook-column CSV source.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Save the imported appointments and report added, duplicate and unreadable counts.
  kind: product
  entities:
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
  contexts:
    main:
      place: desktop::transfer
  actor: user
references:
- kind: code
  role: implementation
  target: Features/Calendar/IcsTransfer.cs
- kind: code
  role: implementation
  target: Services/IcsService.cs
- kind: code
  role: implementation
  target: Services/CsvService.cs
- kind: code
  role: implementation
  target: Services/EmlService.cs
- kind: code
  role: implementation
  target: Services/EventStore.Categories.cs
- kind: code
  role: implementation
  target: Shell/SecurityHost.cs
---

# Import Outlook-column CSV

## Trigger

The User chooses a CSV containing Subject and Start Date columns.

## Outcome

Plain appointments are imported. Column matching ignores case and column order; additional columns are ignored except supported fields.

## Edge cases

- Only Subject and Start Date headers are mandatory.
- An all-day CSV end is inclusive and becomes an exclusive ending midnight.
- A missing timed start time becomes midnight; a missing or non-increasing end becomes one hour after the start.
- Duplicate identity uses title, start, end and location; repeating an identical row does not overwrite existing details.
- Attendees and recurrence patterns are not imported from CSV.
