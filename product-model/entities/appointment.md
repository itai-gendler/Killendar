---
references:
- kind: code
  role: implementation
  target: Models/CalendarEvent.cs
- kind: code
  role: implementation
  target: Features/Appointments/AppointmentEditor.cs
- kind: code
  role: implementation
  target: Services/EventStore.Persistence.cs
---

# Appointment

A separately saved appointment that does not repeat.

## Information kept

- **Title** — The appointment subject.
- **Start** — The starting local date and time, or first all-day date.
- **End** — The ending local date and time; all-day spans end at the midnight after the last covered date.
- **All day** — Whether the entry covers whole calendar dates.
- **Location** — Free text describing where it happens.
- **Description** — Additional appointment text.
- **Attendees** — The entered attendee names or addresses.
- **Categories** — An ordered list of assigned category names.
- **Created** — When the entry was first saved.
- **Modified** — When its appointment details were last saved.
