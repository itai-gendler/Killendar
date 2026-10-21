---
appliesTo:
- type: entity
  id: appointment
  facts:
  - Title
  - Start
  - End
- type: entity
  id: repeating-series
  facts:
  - Title
  - Start
  - End
- type: entity
  id: single-date-edit
  facts:
  - Title
  - Start
  - End
references:
- kind: code
  role: implementation
  target: Features/Appointments/AppointmentEditor.cs
---

# Saved editor entries have a title and readable dates

Desktop saves require a nonblank title and readable dates. Timed end must follow start. A selected repeat count must be positive and a selected end date readable. Errors keep the editor open. Imported data is interpreted under its own format rules.
