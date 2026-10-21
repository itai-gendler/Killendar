---
appliesTo:
- type: entity
  id: appointment
  facts:
  - Start
  - End
  - All day
- type: entity
  id: repeating-series
  facts:
  - Start
  - End
  - All day
- type: entity
  id: single-date-edit
  facts:
  - Start
  - End
  - All day
references:
- kind: code
  role: implementation
  target: Services/CalendarDateSpan.cs
- kind: code
  role: implementation
  target: Services/EventStore.cs
- kind: code
  role: implementation
  target: Services/CsvService.cs
- kind: code
  role: implementation
  target: Services/IcsService.cs
- kind: code
  role: implementation
  target: Services/CalendarCommands.cs
---

# All-day dates retain their calendar meaning

All-day spans keep floating dates and an exclusive ending midnight. The desktop editor and CSV expose an inclusive last covered date; ICS and command-line creation use the exclusive end. Timed entries keep their moment in time and are shown in the local time zone, so a Killendar carried to another time zone still shows the right times.
