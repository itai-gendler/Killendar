---
appliesTo:
- type: entity
  id: repeating-series
  facts:
  - End condition
  - Skipped dates
references:
- kind: code
  role: implementation
  target: Services/Recurrence.cs
- kind: code
  role: implementation
  target: Shell/RepeatPanel.cs
---

# A deleted date still counts toward a series that ends after a number of times

A series ends Never, After a number of times, or On a date. The number counts every date the pattern generates from its start, including dates deleted one at a time: deleting one date of a ten-time series leaves nine, and adds no date at the end. An end date is inclusive.
