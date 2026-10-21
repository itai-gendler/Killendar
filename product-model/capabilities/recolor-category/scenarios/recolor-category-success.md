---
kind: primary
routes:
  main: Desktop
steps:
- text: Choose a replacement color and accept it.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::categories
  actor: user
- text: Save the category color and refresh its use in the calendar.
  kind: product
  entities:
  - entity: category
    effect: changes
    facts:
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
- kind: code
  role: implementation
  target: Services/CategoryManager.cs
---

# Recolor a category

## Trigger

The User picks a new color for a category and accepts it.

## Outcome

The new color is saved, and every appointment whose primary category it is takes it.
