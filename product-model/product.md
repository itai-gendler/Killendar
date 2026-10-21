---
id: killendar
summary: A Windows calendar with local Killendar files, repeating appointments, calendar exchange and
  optional encryption.
category: productivity
tags:
- calendar
- appointments
- local-files
authors:
- name: Steve the Killer
  url: https://github.com/SteveTheKiller
license: GPL-3.0-only
languages:
- en-US
- es
- zh-TW
- zh-CN
- bn
- tr-TR
- de-DE
- fr-FR
- ja-JP
- cs-CZ
- pl-PL
- hu-HU
- it-IT
- ru-RU
- kk-KZ
- vi-VN
- uk-UA
- nb-NO
- pt-BR
limitations:
- Killendar runs on Windows 10 or 11 for x64.
- There are no product accounts, cloud synchronization, or telemetry.
- Recurrence uses daily, weekly, same-date monthly, or yearly patterns.
- Saved email invitations are imported from EML; binary Outlook MSG files are not supported.
- Calendar printing is performed from the exported HTML page in a browser.
references:
- kind: doc
  role: intent
  target: README.md
- kind: doc
  role: intent
  target: CHANGELOG.md
- kind: code
  role: implementation
  target: Services/Recurrence.cs
- kind: code
  role: implementation
  target: Services/EmlService.cs
- kind: code
  role: implementation
  target: Services/HtmlExport.cs
---

# Killendar

A free and open-source calendar for Windows that keeps appointments in files on your own machine. A Killendar holds appointments, repeating series, single-date edits and color categories. People can keep several Killendars, exchange calendar data with other programs, and choose password protection for each file.

## Intent

In the project's words, Killendar is a "free and open-source calendar for Windows with no account, no sync, and no telemetry." "Your appointments live in a single `.kcal` file on your own machine - an ordinary SQLite database until you put a password on it." Encryption is opt-in: "the lock button puts a password on a Killendar and it is encrypted at rest." Around that file it offers the everyday calendar: four views, repeating appointments with per-date exceptions, color categories, and import and export "in the formats people actually hand you."
