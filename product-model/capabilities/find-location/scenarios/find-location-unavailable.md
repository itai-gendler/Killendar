---
kind: edge
routes:
  main: Desktop
steps:
- text: Enter a location query while suggestions are enabled.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Retain the input when no current lookup result is available.
  kind: product
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

# Keep typed text without suggestions

## Trigger

The lookup fails or returns no addresses.

## Outcome

The suggestion list closes and the typed location remains available for editing and saving.

## Edge cases

- Typing a shorter query or disabling suggestions closes the list.
- A response for an earlier query is ignored when the text has changed.
