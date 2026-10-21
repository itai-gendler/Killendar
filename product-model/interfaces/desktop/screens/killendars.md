---
entities:
- entity: killendar
  shows:
  - Name
  - File location
  - Size
  - Last changed
  - Password protection
  - Session access
  - Active
  collects:
  - Name
- entity: preferences
  shows:
  - Data folder
  collects:
  - Data folder
references:
- kind: code
  role: implementation
  target: Controls/KillendarsDialog.xaml.cs
---

# Manage Killendars

Inspect and act on calendar files in the selected data folder.
