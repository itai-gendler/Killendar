---
kind: alternate
routes:
  main: Desktop
steps:
- text: Confirm deletion of the whole series.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Remove the repeating series and its single-date edits.
  kind: product
  entities:
  - entity: repeating-series
    effect: removes
  - entity: single-date-edit
    effect: removes
    with: repeating-series
  contexts:
    main:
      place: desktop::appointment
  actor: user
references:
- kind: code
  role: implementation
  target: Features/Appointments/AppointmentEditor.cs
- kind: code
  role: implementation
  target: Services/EventStore.Persistence.cs
- kind: code
  role: implementation
  target: Shell/RepeatPanel.cs
---

# Delete a whole series and its single-date edits

## Trigger

The User opens a generated date or saved single-date edit, selects whole-series scope and confirms deletion.

## Outcome

The repeating series and all its single-date edits are removed together.
