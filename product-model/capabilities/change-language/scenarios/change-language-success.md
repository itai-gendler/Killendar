---
kind: primary
routes:
  main: Desktop
steps:
- text: Select an interface language.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::language
  actor: user
- text: Save the Preferences language and refresh the interface and calendar headings.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Language
  contexts:
    main:
      place: desktop::language
  actor: user
references:
- kind: code
  role: implementation
  target: Services/LocaleManager.cs
- kind: code
  role: implementation
  target: Shell/Language.cs
---

# Change language

## Trigger

The User picks one of the nineteen interface languages.

## Outcome

The language is saved and the interface, including calendar headings, switches without a restart.
