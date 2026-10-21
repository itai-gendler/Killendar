---
kind: primary
routes:
  main: Desktop
steps:
- text: Confirm deletion of the selected color definition.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::categories
  actor: user
- text: Remove the category and its assignments from appointments, repeating series and single-date edits.
  kind: product
  entities:
  - entity: category
    effect: removes
  - entity: appointment
    effect: changes
    facts:
    - Categories
  - entity: repeating-series
    effect: changes
    facts:
    - Categories
  - entity: single-date-edit
    effect: changes
    facts:
    - Categories
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

# Delete a category

## Trigger

The User deletes a category in Categories and confirms.

## Outcome

The definition is gone and the name is removed from every appointment, series and single-date edit that had it; none of them is deleted.
