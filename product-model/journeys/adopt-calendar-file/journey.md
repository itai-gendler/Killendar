---
actors:
- user
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
---

# Use a calendar opened from a file

## Goal

Bring an external calendar into local storage and open it.

## Success criterion

The local copy is active and readable.
