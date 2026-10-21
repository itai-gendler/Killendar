---
kind: primary
routes:
  main: Desktop
steps:
- text: Enter a nonempty name and choose a color.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::categories
  actor: user
- text: Create the category with its name and color.
  kind: product
  entities:
  - entity: category
    effect: creates
    facts:
    - Name
    - Color
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

# Add a category

## Trigger

The User types a new category name in Categories and picks its color.

## Outcome

The open Killendar has a new category definition with that name and color, and the appointment editor offers it.
