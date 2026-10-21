---
kind: alternate
routes:
  main: Desktop
steps:
- text: Enable close-to-tray.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::about
  actor: user
- text: Save the Preferences close-to-tray choice.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Close to system tray
  contexts:
    main:
      place: desktop::about
  actor: user
- text: Close the main window.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::calendar
  actor: user
- text: Read Preferences and hide the window while keeping the session.
  kind: product
  entities:
  - entity: preferences
    effect: reads
    facts:
    - Close to system tray
  contexts:
    main:
      place: desktop::calendar
  actor: user
references:
- kind: code
  role: implementation
  target: Features/About/AboutController.cs
- kind: code
  role: implementation
  target: Services/StartupRegistration.cs
- kind: code
  role: implementation
  target: Shell/CloseToTray.cs
- kind: code
  role: implementation
  target: Shell/LocationLookup.cs
---

# Close to the system tray

## Trigger

The User enables close-to-tray and later closes the window.

## Outcome

Closing hides the window while keeping the session. The tray’s Open action restores it; Exit quits. With the setting off, closing exits.
