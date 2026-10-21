---
kind: primary
routes:
  main: Desktop
steps:
- text: Create a new calendar file.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
- text: Create a uniquely named plaintext Killendar and offer its name for editing.
  kind: product
  entities:
  - entity: killendar
    effect: creates
    facts:
    - Name
    - File location
    - Size
    - Last changed
    - Password protection
    - Session access
    - Active
    to: Plaintext
  contexts:
    main:
      place: desktop::killendars
  actor: user
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

# Create a Killendar

## Trigger

The User chooses New Killendar in Manage Killendars.

## Outcome

An empty Killendar without a password is added to the data folder under a unique name, with its name ready to edit.
