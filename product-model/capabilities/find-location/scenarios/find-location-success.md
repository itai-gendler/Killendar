---
kind: primary
routes:
  main: Desktop
steps:
- text: Enter a location query.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Read Preferences and request matching addresses from Photon.
  kind: product
  entities:
  - entity: preferences
    effect: reads
    facts:
    - Address suggestions
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Select a suggested address to fill the location field.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
references:
- kind: code
  role: implementation
  target: Shell/LocationLookup.cs
---

# Choose an address suggestion

## Trigger

Address suggestions are enabled and the User pauses after entering at least three characters.

## Outcome

The current matching suggestions are shown. Selecting one fills the location field without saving an appointment.
