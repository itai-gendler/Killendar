---
appliesTo:
- type: entity
  id: killendar
  facts:
  - Name
  - File location
- type: entity
  id: preferences
  facts:
  - Data folder
references:
- kind: code
  role: implementation
  target: Services/EventStore.Catalog.cs
- kind: code
  role: implementation
  target: Services/EventStore.cs#SetDataDir
- kind: code
  role: implementation
  target: Controls/KillendarsDialog.xaml.cs
---

# External Killendars are copied into the data folder

Adopting an external calendar copies it into the configured folder without altering the source. Existing catalog files are reused. A colliding name receives a suffix. Changing the data folder changes the catalog selection and does not move existing files.
