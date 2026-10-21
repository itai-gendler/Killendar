---
entities:
- entity: appointment
  shows: &id001
  - Title
  - Start
  - End
  - All day
  - Location
  - Description
  - Attendees
  - Categories
- entity: repeating-series
  shows: *id001
- entity: single-date-edit
  shows: *id001
- entity: killendar
  shows:
  - Name
  - Active
- entity: preferences
  shows:
  - Work week
  - Month mode
  - Visible weeks
  - Calendar density
  - Sidebar detail
  collects:
  - Work week
  - Month mode
  - Visible weeks
  - Calendar density
  - Sidebar detail
references:
- kind: code
  role: implementation
  target: Features/Calendar/CalendarController.cs
- kind: code
  role: implementation
  target: Shell/DayAgendaPanel.cs
- kind: code
  role: implementation
  target: Views/AgendaView.cs
---

# Calendar

Month, Week, Day and Agenda views of the open calendar, including the selected day’s agenda. Generated dates and single-date edits appear on their applicable dates.
