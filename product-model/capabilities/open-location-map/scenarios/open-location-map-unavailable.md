---
kind: edge
routes:
  main: Desktop
steps:
- text: Request the maps search.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::appointment
  actor: user
- text: Keep the location text in the editor.
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

# Retain a location when the browser cannot open

## Trigger

The User requests a maps search but the operating system cannot open the destination.

## Outcome

No map opens; the location remains in the editor.
