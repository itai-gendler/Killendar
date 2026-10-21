---
appliesTo:
- type: entity
  id: repeating-series
  facts:
  - Frequency
  - Interval
  - Weekdays
references:
- kind: code
  role: implementation
  target: Services/Recurrence.cs
---

# Repeats land on matching calendar dates

Daily, weekly, monthly and yearly patterns advance by the chosen positive interval. Monthly dates absent from a month and yearly February 29 dates absent from a year are skipped rather than shifted. Weekly empty weekday selection uses the starting weekday.
