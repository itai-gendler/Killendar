---
appliesTo:
- type: entity
  id: category
- type: entity
  id: appointment
  facts:
  - Categories
- type: entity
  id: repeating-series
  facts:
  - Categories
- type: entity
  id: single-date-edit
  facts:
  - Categories
references:
- kind: code
  role: implementation
  target: Controls/CategoriesDialog.xaml.cs
- kind: code
  role: implementation
  target: Services/EventStore.Categories.cs
- kind: code
  role: implementation
  target: Shell/Categories.cs
---

# Category names are unique within one Killendar

Category definitions have nonempty names without commas and are unique ignoring case. Assignments are trimmed, preserve order and discard duplicate names ignoring case. The first name is primary. Renaming a definition rewrites assignments; deleting it removes assignments without deleting appointments.
