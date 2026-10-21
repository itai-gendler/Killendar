---
kind: edge
routes:
  main: Desktop
steps:
- text: Preview a different color and cancel.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::categories
  actor: user
- text: Restore the saved category color.
  kind: product
  entities:
  - entity: category
    effect: reads
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

# Cancel a color preview

## Trigger

The User previews another color and then cancels.

## Outcome

The original category color is restored and no new color is saved.
