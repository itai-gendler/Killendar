---
kind: primary
routes:
  main: Desktop
steps:
- text: Request a map search for the current nonempty location text.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Open the browser search using the entered location; the editor text remains available.
  kind: product
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
references:
- kind: code
  role: implementation
  target: Shell/LocationMap.cs
---

# Open a location on a map

## Trigger

The appointment editor has location text, and the User asks to see it on a map.

## Outcome

A maps search for that location opens in the default browser, and the editor keeps its text.
