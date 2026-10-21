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
- text: Retain the Installation version and open the release page after failure.
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

# Fall back after a failed download or verification

## Trigger

The update download or checksum verification fails.

## Outcome

The current application remains open and the releases page opens for manual follow-up.
