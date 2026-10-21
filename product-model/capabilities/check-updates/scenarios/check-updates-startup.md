---
kind: alternate
routes:
  main: Desktop
steps:
- text: Preferences enable startup checking for this run.
  kind: condition
  entities:
  - entity: preferences
    effect: reads
    facts:
    - Startup update check
  contexts:
    main:
      place: desktop::calendar
  unattended: true
- text: Check the Installation version and retain a newer available version.
  kind: product
  entities:
  - entity: installation
    effect: changes
    facts:
    - Available version
  contexts:
    main:
      place: desktop::about
references:
- kind: code
  role: implementation
  target: Features/About/AboutController.cs
- kind: code
  role: implementation
  target: Services/UpdateService.cs
---

# Check once after startup

## Trigger

A normal desktop run has opened its calendar and startup checking is enabled.

## Outcome

A newer version becomes available in About. A confirmation offer appears only while the main window is visible and no owned dialog is open.
