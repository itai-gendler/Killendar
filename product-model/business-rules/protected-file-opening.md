---
appliesTo:
- type: entity
  id: killendar
references:
- kind: code
  role: implementation
  target: Features/Security/SecurityController.cs
- kind: code
  role: implementation
  target: Services/EventStore.Encryption.cs
- kind: code
  role: implementation
  target: Services/EventStore.cs
---

# Protected calendars open after password verification

An encrypted file’s password must successfully open that file before its contents become the desktop calendar. A rejected password returns to the prompt. Starting fresh preserves the old locked file under another name.
