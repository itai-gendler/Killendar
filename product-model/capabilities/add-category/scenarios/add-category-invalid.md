---
kind: validation
routes:
  main: Desktop
steps:
- text: Submit a blank or duplicate name.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::categories
  actor: user
- text: Report the name problem.
  kind: product
  entities: []
  contexts:
    main:
      place: desktop::categories
  actor: user
references:
- kind: code
  role: implementation
  target: Controls/CategoriesDialog.xaml.cs
- kind: code
  role: implementation
  target: Services/EventStore.Categories.cs
---

# Reject a missing or duplicate category name

## Trigger

The User adds a blank name or a name already defined, ignoring case.

## Outcome

No definition is added and Categories reports the problem. Commas are dropped from an entered name, because they separate the names assigned to an appointment.
