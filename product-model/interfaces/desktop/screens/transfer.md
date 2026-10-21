---
entities:
- entity: killendar
  shows:
  - Name
- entity: preferences
  shows:
  - Export reminder
  collects:
  - Export reminder
references:
- kind: code
  role: implementation
  target: Features/Calendar/IcsTransfer.cs
---

# Import and export

Choose a source calendar file or an export format, destination and whole-calendar or date-range scope. The process reports its result and import counts.
