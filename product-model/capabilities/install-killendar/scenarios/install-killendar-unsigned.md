---
kind: validation
routes:
  main: Desktop
steps:
- text: Request installation of a copy without a valid signature.
  kind: actor
  entities:
  - entity: installation
    effect: reads
    facts: []
  contexts:
    main:
      place: desktop::installation
  actor: user
- text: Report that installation was refused.
  kind: product
  entities:
  - entity: installation
    effect: reads
    facts: []
  contexts:
    main:
      place: desktop::installation
  actor: user
references:
- kind: code
  role: implementation
  target: App.Installation.cs
- kind: code
  role: implementation
  target: Shell/Install.cs
- kind: code
  role: implementation
  target: App.xaml.cs
---

# Refuse installation of an unsigned copy

## Trigger

The running copy has no valid signature.

## Outcome

Installation is refused with an explanation; silent installation returns a rejection status.
