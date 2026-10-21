---
kind: primary
routes:
  main: Desktop
steps:
- text: Confirm the offered release.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::about
  actor: user
- text: Download and verify the release, then change the Installation version and relaunch.
  kind: product
  entities:
  - entity: installation
    effect: changes
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

# Install a confirmed newer release

## Trigger

The User accepts the update offered in About or after startup.

## Outcome

The newer copy replaces the current executable and relaunches. Installed version metadata follows the new release; a portable copy remains portable.
