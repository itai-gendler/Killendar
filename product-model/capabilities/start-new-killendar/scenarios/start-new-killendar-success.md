---
kind: primary
routes:
  main: Desktop
steps:
- text: Choose the unlock prompt's option to start a new calendar, and confirm.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::password
  actor: user
- text: Rename the locked Killendar aside, still encrypted, and open a new empty Killendar with the starter categories under its original name.
  kind: product
  entities:
  - entity: killendar
    effect: changes
    facts:
    - Name
    - File location
    - Active
    - Session access
    as: old
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
    as: new
  - entity: category
    effect: creates
    facts:
    - Name
    - Color
    with: new
  contexts:
    main:
      place: desktop::calendar
  actor: user
references:
- kind: code
  role: implementation
  target: Features/Security/SecurityController.cs
- kind: code
  role: implementation
  target: Services/EventStore.Encryption.cs
---

# Preserve the locked file and start fresh

## Trigger

The User cannot unlock the active Killendar, for example after forgetting its password, and chooses New Killendar at the unlock prompt.

## Outcome

The locked Killendar is kept, still encrypted, under its name with "-locked-" and a timestamp added. A new empty Killendar without a password opens in its place, under the original name, with the six starter categories.

## Edge cases

- Declining the confirmation returns to the unlock prompt.
