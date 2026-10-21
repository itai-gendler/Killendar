---
appliesTo:
- type: entity
  id: preferences
  facts:
  - Calendar density
references:
- kind: code
  role: implementation
  target: Views/CalendarChrome.cs
- kind: code
  role: implementation
  target: Views/TimeGridView.Interaction.cs
- kind: code
  role: implementation
  target: Shell/Density.cs
---

# New time slots follow the selected grid subdivision

The four density levels provide hour, half-hour, twenty-minute and quarter-hour subdivisions. Creating a timed entry uses the displayed subdivision. Moving an existing entry uses at least half-hour precision even at hour-only density, and follows finer subdivisions at higher density. Month density changes detail rather than selectable dates.
