---
appliesTo:
- type: entity
  id: preferences
  facts:
  - Work week
  - Week start
references:
- kind: code
  role: implementation
  target: Views/TimeGridViews.cs
- kind: code
  role: implementation
  target: Shell/WorkWeek.cs
---

# A work week is Monday through Friday

The five-day Week choice always uses Monday through Friday, independently of the selected first day of week. Month, Day and Agenda do not change their ranges because of this choice.
