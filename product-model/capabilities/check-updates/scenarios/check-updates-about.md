---
kind: primary
routes:
  main: Desktop
steps:
- text: Open About to inspect the running copy.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::about
  actor: user
- text: Compare the Installation version with the latest release and retain its available version.
  kind: product
  entities:
  - entity: installation
    effect: changes
    facts:
    - Available version
  contexts:
    main:
      place: desktop::about
  actor: user
references:
- kind: code
  role: implementation
  target: Features/About/AboutController.cs
- kind: code
  role: implementation
  target: Services/UpdateService.cs
---

# Find a newer release from About

## Trigger

The User opens About.

## Outcome

A newer available version is shown when found.
