---
kind: primary
routes:
  main: Desktop
steps:
- text: Choose installation scope and confirm.
  kind: actor
  entities:
  - entity: installation
    effect: reads
    facts: []
  contexts:
    main:
      place: desktop::installation
  actor: user
- text: Install the signed copy and change the Installation scope.
  kind: product
  entities:
  - entity: installation
    effect: changes
    facts:
    - Scope
    from: Portable
    to: Installed
  contexts:
    main:
      place: desktop::installation
  actor: user
references:
- kind: code
  role: implementation
  target: App.Installation.cs
- kind: code
  role: implementation
  target: Shell/Install.cs
- kind: code
  role: implementation
  target: App.xaml.cs
---

# Install from the portable application

## Trigger

The User requests installation from a portable copy.

## Outcome

A current-user installation is created with Start Menu integration and optional desktop shortcut, then launched. An all-users choice requests Windows administrator approval and uses the machine-wide location.

## Edge cases

- Canceling keeps the portable copy running.
- A failed installation reopens the calendar and reports failure.
