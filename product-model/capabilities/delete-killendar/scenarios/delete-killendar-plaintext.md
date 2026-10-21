---
kind: primary
routes:
  main: Desktop
steps:
- text: Confirm deleting the selected calendar file.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Remove the Killendar and its appointments, repeating series, single-date edits and categories.
  kind: product
  entities:
  - entity: killendar
    effect: removes
    from: Plaintext
  - entity: appointment
    effect: removes
    with: killendar
  - entity: repeating-series
    effect: removes
    with: killendar
  - entity: single-date-edit
    effect: removes
    with: killendar
  - entity: category
    effect: removes
    with: killendar
  contexts:
    main:
      place: desktop::killendars
  actor: user
references:
- kind: code
  role: implementation
  target: Controls/KillendarsDialog.xaml.cs
- kind: code
  role: implementation
  target: Services/EventStore.Catalog.cs
- kind: code
  role: implementation
  target: Features/Security/SecurityController.cs
---

# Delete a plaintext Killendar

## Trigger

The User confirms deleting a selected file.

## Outcome

The selected Killendar and its contents are removed. Canceling confirmation preserves it.
