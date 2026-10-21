---
kind: alternate
routes:
  main: Desktop
steps:
- text: Choose a saved email invitation.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Read the calendar body and save its appointments, repeating series and single-date edits.
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

# Import a saved email invitation

## Trigger

The User chooses an EML file containing calendar invitation text.

## Outcome

The first calendar body is decoded and passed through the same iCalendar import behavior, including counts and recurrence handling.

## Edge cases

- Nested MIME bodies, base64 and quoted-printable calendar parts are supported.
- An unencoded calendar block can also be extracted from the message text.
