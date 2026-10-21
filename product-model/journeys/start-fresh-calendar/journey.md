---
actors:
- user
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

# Start over from a locked Killendar

## Goal

Start a fresh calendar from a locked file and reach the empty schedule.

## Success criterion

The new calendar is open while the previous file is retained aside.
