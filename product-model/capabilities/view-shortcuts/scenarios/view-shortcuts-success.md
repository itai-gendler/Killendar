---
kind: primary
routes:
  main: Desktop
steps:
- text: Open the keyboard shortcut reference.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::shortcuts
  actor: user
- text: Show the available bindings.
  kind: product
  entities: []
  contexts:
    main:
      place: desktop::shortcuts
  actor: user
references:
- kind: code
  role: implementation
  target: Shell/Shortcuts.cs
- kind: code
  role: implementation
  target: Shell/ShortcutsOverlay.cs
---

# View keyboard shortcuts

## Trigger

The User presses F1.

## Outcome

The overlay lists every keyboard binding, as a list or on a drawn keyboard. Single-letter shortcuts never fire while the User is typing in a text field.
