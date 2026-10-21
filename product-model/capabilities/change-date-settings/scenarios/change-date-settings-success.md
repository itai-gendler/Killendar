---
kind: primary
routes:
  main: Desktop
steps:
- text: Choose a date format or first day of week.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::date-settings
  actor: user
- text: Save the Preferences date format and week start choices; refresh calendar headings and readable
    editor dates.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Date format
    - Week start
  contexts:
    main:
      place: desktop::date-settings
  actor: user
references:
- kind: code
  role: implementation
  target: Controls/DateSettingsMenu.cs
- kind: code
  role: implementation
  target: Services/DateFormatManager.cs
- kind: code
  role: implementation
  target: Services/WeekStartManager.cs
- kind: code
  role: implementation
  target: Shell/Language.cs
---

# Change date settings

## Trigger

The User picks a date format (ISO, US, UK/EU or Follow Windows) or a first day of the week (Follow Windows, Sunday or Monday).

## Outcome

The choice is saved; calendar headings and the dates the editor shows and reads follow it, whatever the interface language.
