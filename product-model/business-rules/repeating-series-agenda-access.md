---
appliesTo:
- type: entity
  id: repeating-series
  effect: reads
  contexts:
  - place: command-line
permits:
- actors:
  - user
  when:
  - entity: killendar
    fact: Password protection
    is: false
references:
- kind: code
  role: implementation
  target: Killendar.Cli/Program.cs#Agenda
- kind: code
  role: implementation
  target: Services/EventStore.cs#OpenReadOnly
---

# The command-line agenda reads repeating series only from a Killendar without a password

The agenda reads an existing plaintext Killendar on its own, whether or not the desktop has it open, and never asks for a password.
