---
appliesTo:
- type: entity
  id: installation
  facts:
  - Available version
- type: entity
  id: preferences
  facts:
  - Startup update check
references:
- kind: code
  role: implementation
  target: Features/About/AboutController.cs
- kind: code
  role: implementation
  target: Services/UpdateService.cs
---

# Killendar looks for a newer release on its own only while the startup check is on

With "Check for updates on startup" on, a normal launch checks once after the calendar opens; opening About checks whatever the setting. A found release is only offered: installing it always waits for the User to confirm.
