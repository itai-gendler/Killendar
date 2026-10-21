---
relations:
- entity: single-date-edit
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: Models/CalendarEvent.cs
- kind: code
  role: implementation
  target: Services/Recurrence.cs
- kind: code
  role: implementation
  target: Services/EventStore.Persistence.cs
---

# Repeating series

One saved repeating appointment whose dates are generated for the requested calendar range.

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
- **Frequency** — Daily, weekly, monthly on the same date, or yearly.
- **Interval** — The number of days, weeks, months or years between repeats; at least one.
- **Weekdays** — Selected weekdays for a weekly pattern; an empty selection uses the starting weekday.
- **End condition** — Never, after a positive occurrence count, or through an inclusive calendar date.
- **Skipped dates** — Original calendar dates removed individually from the schedule.
