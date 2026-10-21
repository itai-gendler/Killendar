---
kind: validation
routes:
  main: Desktop
steps:
- text: Submit a blank, unchanged or duplicate name.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::categories
  actor: user
- text: Retain the category name.
  kind: product
  entities:
  - entity: category
    effect: reads
    facts:
    - Name
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

# Keep the old category name

## Trigger

The proposed name is blank, unchanged, or belongs to another definition.

## Outcome

The old name remains; a duplicate reports a conflict. Canceling a rename also keeps the old name.
