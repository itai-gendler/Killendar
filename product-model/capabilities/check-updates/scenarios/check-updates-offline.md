---
kind: edge
routes:
  main: Desktop
steps:
- text: Open About while the release service is unavailable.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::about
  actor: user
- text: Keep the current Installation version.
  kind: product
  entities:
  - entity: installation
    effect: reads
    facts:
    - Version
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

# Continue without an update offer

## Trigger

A release check cannot reach the service or finds no newer version.

## Outcome

The calendar stays usable and no update is offered; a failed check shows no error.
