---
appliesTo:
- type: entity
  id: repeating-series
  facts:
  - Start
  - End
  - Skipped dates
- type: entity
  id: single-date-edit
  facts:
  - Start
  - End
references:
- kind: code
  role: implementation
  target: Services/EventStore.Persistence.cs#UpdateSeries
- kind: code
  role: implementation
  target: Features/Calendar/CalendarController.cs
---

# A later occurrence edit retains the series anchor

Applying a whole-series edit from a generated occurrence shifts the original series start by the edited occurrence offset. Whole-day offsets shift skipped dates with it. Moving one date directly creates or changes only its replacement.
