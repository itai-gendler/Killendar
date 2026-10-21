---
appliesTo:
- type: entity
  id: installation
  effect: changes
  to: Installed
references:
- kind: code
  role: implementation
  target: App.Installation.cs#DoInstall
- kind: code
  role: implementation
  target: App.Installation.cs#DoSilentInstall
---

# Only a copy with a valid signature is installed

Installing, interactively or silently, first checks the running copy’s signature; an unsigned copy keeps running portable and is not installed.
