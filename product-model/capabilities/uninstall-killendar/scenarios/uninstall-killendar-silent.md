---
kind: alternate
routes:
  main: Command line
steps:
- text: Invoke silent uninstallation.
  kind: actor
  entities: []
  contexts:
    main:
      place: command-line
  actor: user
- text: Change the Installation scope to removed.
  kind: product
  entities:
  - entity: installation
    effect: changes
    facts:
    - Scope
    from: Installed
    to: Removed
  contexts:
    main:
      place: command-line
  actor: user
references:
- kind: code
  role: implementation
  target: App.Installation.cs#Uninstall
- kind: code
  role: implementation
  target: App.xaml.cs
---

# Uninstall silently

## Trigger

The User, a package manager or a deployment tool runs Killendar with the silent uninstall option.

## Outcome

The installed program, shortcuts, startup entry and installation registrations are removed. Profile calendar files remain.

## Edge cases

- Removing an all-users installation asks Windows for administrator approval when the process is not already elevated.
