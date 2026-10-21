---
kind: alternate
routes:
  main: Desktop
steps:
- text: Launch the calendar for the first time.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::calendar
  actor: user
- text: Create and open the default Killendar with its initial categories.
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
  - entity: category
    effect: creates
    facts:
    - Name
    - Color
    with: killendar
  contexts:
    main:
      place: desktop::calendar
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
- kind: code
  role: implementation
  target: Services/EventStore.cs
- kind: code
  role: implementation
  target: Services/EventStore.Schema.cs
---

# Open the first empty calendar

## Trigger

The User launches the application with no existing active file or legacy data.

## Outcome

Default opens as an empty plaintext calendar with six initial category definitions.
