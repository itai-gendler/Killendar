---
kind: primary
routes:
  main: Desktop
steps:
- text: Enter a different nonempty category name.
  kind: actor
  entities:
  - entity: category
    effect: reads
    facts:
    - Name
  contexts:
    main:
      place: desktop::categories
  actor: user
- text: Rename the category and rewrite its name on appointments, repeating series and single-date edits.
  kind: product
  entities:
  - entity: category
    effect: changes
    facts:
    - Name
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

# Rename a category

## Trigger

The User gives a category a new name that no other category has.

## Outcome

The category has the new name, and every appointment, series and single-date edit that carried the old name now carries the new one. Their last-modified times stay as they were.
