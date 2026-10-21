---
entities:
- entity: installation
  shows:
  - Version
  - Release date
  - Publisher
  - Certificate thumbprint
  - Executable hash
  - Available version
- entity: preferences
  shows:
  - Address suggestions
  - Startup update check
  - Start with Windows
  - Close to system tray
  collects:
  - Address suggestions
  - Startup update check
  - Start with Windows
  - Close to system tray
references:
- kind: code
  role: implementation
  target: Features/About/AboutController.cs
- kind: code
  role: implementation
  target: Shell/LocationLookup.cs
---

# About

Read the running version and publisher information, act on available updates and change startup and address lookup choices.
