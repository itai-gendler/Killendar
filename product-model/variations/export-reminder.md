---
kind: configuration
of: capability-scenario
settings:
- entity: preferences
  fact: Export reminder
takesEffect: The reminder choice is read when an export begins, after scope selection.
stability: The decision applies to that export attempt; a saved suppression affects later attempts.
alternatives:
- id: export-appointments-reminder
  selectedWhen: The current calendar is protected and reminder suppression is not enabled; missing suppression
    uses this reminder.
- id: export-appointments-without-reminder
  selectedWhen: Reminder suppression is enabled, or the current calendar has no password protection.
references:
- kind: code
  role: implementation
  target: Features/Calendar/IcsTransfer.cs#ConfirmPlaintextExport
---

# Export reminder

The stored reminder preference determines whether an applicable export requires the reminder confirmation.
