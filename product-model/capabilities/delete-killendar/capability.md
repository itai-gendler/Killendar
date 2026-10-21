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

# Delete Killendar

Delete a selected calendar file after confirmation. Deleting the active selection retargets another remaining file, or Default when none remain.
