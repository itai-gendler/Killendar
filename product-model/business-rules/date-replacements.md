---
appliesTo:
- type: entity
  id: single-date-edit
- type: entity
  id: repeating-series
references:
- kind: code
  role: implementation
  target: Services/EventStore.Persistence.cs#SaveOccurrence
- kind: code
  role: implementation
  target: Services/EventStore.Queries.cs#GetInRange
---

# A single-date edit stands for exactly one original date of its series

A single-date edit replaces its original date even when moved to another day. It never repeats on its own. Saving another edit for that same original date changes the existing single-date edit rather than adding a second one.
