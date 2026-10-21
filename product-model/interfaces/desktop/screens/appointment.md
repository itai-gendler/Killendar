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
  collects: *id001
- entity: repeating-series
  shows:
  - Title
  - Start
  - End
  - All day
  - Location
  - Description
  - Attendees
  - Categories
  - Frequency
  - Interval
  - Weekdays
  - End condition
  collects:
  - Title
  - Start
  - End
  - All day
  - Location
  - Description
  - Attendees
  - Categories
  - Frequency
  - Interval
  - Weekdays
  - End condition
- entity: single-date-edit
  shows: *id001
  collects: *id001
- entity: category
  shows:
  - Name
  - Color
references:
- kind: code
  role: implementation
  target: Features/Appointments/AppointmentEditor.cs
- kind: code
  role: implementation
  target: Shell/RepeatPanel.cs
- kind: code
  role: implementation
  target: Shell/Categories.cs
---

# Appointment editor

Compose or edit the selected appointment or repeating date. A repeating date offers just-this-date and whole-series scope; only whole-series scope offers the repeat pattern.
