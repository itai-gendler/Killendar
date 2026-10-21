---
appliesTo:
- type: entity
  id: category
- type: entity
  id: killendar
references:
- kind: code
  role: implementation
  target: Services/EventStore.Schema.cs
- kind: code
  role: implementation
  target: Services/CategoryManager.cs
- kind: code
  role: implementation
  target: Shell/Categories.cs
---

# A new Killendar starts with six categories, and deleted ones stay deleted

A new Killendar gets Red, Orange, Yellow, Green, Blue and Purple. They are its own definitions: reopening it never recreates one the User deleted, and importing an appointment with a category name the Killendar does not define keeps the name on the appointment without adding a definition.
