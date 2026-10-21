---
kind: primary
routes:
  main: Desktop
steps:
- text: Confirm uninstallation.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::installation
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
      place: desktop::installation
  actor: user
references:
- kind: code
  role: implementation
  target: App.Installation.cs#Uninstall
- kind: code
  role: implementation
  target: App.xaml.cs
---

# Uninstall interactively

## Trigger

The User requests removal of the installed application.

## Outcome

The installed program, shortcuts, startup entry and installation registrations are removed. Profile calendar files remain.

## Edge cases

- Machine-wide removal requests Windows administrator approval when required.
- Canceling the interactive confirmation leaves the installation present.
