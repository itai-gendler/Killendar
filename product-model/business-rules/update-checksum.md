---
appliesTo:
- type: entity
  id: installation
  facts:
  - Version
  - Available version
references:
- kind: code
  role: implementation
  target: Services/UpdateService.cs
- kind: code
  role: implementation
  target: Features/About/AboutController.cs
---

# An update is installed only after its checksum matches

The downloaded release must have a matching entry in the published checksum file before it is handed to the replacement helper. The application exits for an update only after the helper starts.
