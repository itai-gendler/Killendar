---
kind: primary
result: achieved
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
  capability: create-killendar
- text: Create the Killendar and offer its name for editing.
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
  capability: create-killendar
- text: Enter the desired file name.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::killendars
  actor: user
  capability: rename-killendar
- text: Rename the Killendar.
  kind: product
  entities:
  - entity: killendar
    effect: changes
    facts:
    - Name
    - File location
  contexts:
    main:
      place: desktop::killendars
  actor: user
  capability: rename-killendar
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

# Create a Killendar and name it

## Trigger

The User chooses to create another calendar.

## Outcome

The new calendar is listed under its chosen name.
