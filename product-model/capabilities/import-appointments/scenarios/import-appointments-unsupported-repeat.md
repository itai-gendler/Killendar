---
kind: alternate
routes:
  main: Desktop
steps:
- text: Choose a file containing an unsupported repeat rule.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::transfer
  actor: user
- text: Save the first appointment and report the unsupported recurrence.
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

# Import an unsupported repeat as one date

## Trigger

An ICS entry has an unsupported recurrence rule, such as an ordinal monthly weekday.

## Outcome

Its readable first appointment is added without a partial repeat rule, and the repeat loss is reported.
