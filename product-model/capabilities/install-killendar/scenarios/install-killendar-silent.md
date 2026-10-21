---
kind: alternate
routes:
  main: Command line
steps:
- text: Invoke silent installation.
  kind: actor
  entities:
  - entity: installation
    effect: reads
    facts: []
  contexts:
    main:
      place: command-line
  actor: user
- text: Install the copy and change the Installation scope.
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
      place: command-line
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

# Install without interactive prompts

## Trigger

The User invokes silent installation.

## Outcome

The signed copy is installed for all users when the process is elevated, otherwise for the current user. Completion is reported by exit status.
