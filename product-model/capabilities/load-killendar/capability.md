---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: Controls/KillendarsDialog.xaml.cs
- kind: code
  role: implementation
  target: Services/EventStore.Catalog.cs
- kind: code
  role: implementation
  target: Features/Security/SecurityController.cs
domain: killendars
---

# Load Killendar

Bring an existing calendar into the data-folder catalog. An external file is copied with a nonconflicting name; a file already in the folder is reused.
