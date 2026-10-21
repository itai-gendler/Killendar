---
kind: edge
routes:
  main: Desktop
steps:
- text: Confirm an available release.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::about
  actor: user
- text: Retain the Installation version after the failed hand-off.
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

# Keep running when the update helper cannot start

## Trigger

The update helper cannot be started, including a declined Windows elevation request.

## Outcome

The download is discarded and the current application remains running with the update action available again.
