---
kind: primary
routes:
  main: Desktop
steps:
- text: Choose an iCalendar source file.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Save imported appointments, repeating series and single-date edits.
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
    with: repeating-series
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

# Import an iCalendar file

## Trigger

The User chooses an ICS file or opens one through its file association.

## Outcome

Supported entries are added; existing ordinary or series identities are skipped. Counts distinguish added entries, skipped duplicates, unreadable entries, unsupported components and unsupported recurrence.

## Edge cases

- Time-zone-qualified dates are converted to local time; date-only entries remain all day.
- An unreadable start is skipped and counted. A missing or non-increasing end defaults to one hour or one all-day date.
- Tasks, journal entries and free/busy components are counted as unsupported. Nested alarm properties do not replace appointment details.
- Unknown category names are retained as assignments without creating definitions.
- Extra recurrence dates supplied as RDATE are reported as recurrence information that could not be retained.
