---
references:
- kind: code
  role: implementation
  target: Models/CalendarEvent.cs
- kind: code
  role: implementation
  target: Services/EventStore.Persistence.cs#SaveOccurrence
---

# Single-date edit

A per-date exception: what saving "Just this date" on one date of a repeating series keeps in place of that date. It remembers the original date even when moved to a different day.

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
- **Original occurrence** — The original starting date and time identifying the date replaced in its series.
