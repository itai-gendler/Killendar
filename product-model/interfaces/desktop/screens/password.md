---
entities:
- entity: killendar
  shows:
  - Name
  - Password protection
  - Session access
references:
- kind: code
  role: implementation
  target: Features/Security/SecurityController.cs
- kind: code
  role: implementation
  target: Controls/PasswordDialog.xaml.cs
---

# Password

Unlock the selected calendar or set, change or remove its password. Starting fresh preserves the locked calendar.
