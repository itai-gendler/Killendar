---
singleton: true
references:
- kind: code
  role: implementation
  target: Settings.cs
- kind: code
  role: implementation
  target: Services/LocaleManager.cs
- kind: code
  role: implementation
  target: Services/DateFormatManager.cs
- kind: code
  role: implementation
  target: Services/WeekStartManager.cs
- kind: code
  role: implementation
  target: Shell/Density.cs
- kind: code
  role: implementation
  target: Shell/LocationLookup.cs
- kind: code
  role: implementation
  target: Features/About/AboutController.cs
- kind: code
  role: implementation
  target: Views/MonthView.xaml.cs
---

# Preferences

The local choices shared across the User’s Killendars.

## Information kept

- **Language** — The selected interface language; initially follows a supported Windows display language, otherwise English.
- **Date format** — ISO by default, or US, UK/EU, or Follow Windows.
- **Week start** — Follow Windows by default, or Sunday or Monday.
- **Work week** — Whether Week view shows Monday through Friday instead of seven days; initially off.
- **Month mode** — Calendar month or rolling weeks; initially calendar month.
- **Visible weeks** — One to six weeks for rolling Month view; initially four.
- **Calendar density** — One of four levels, controlling time-slot subdivisions and month detail.
- **Sidebar detail** — One of four detail levels for the day agenda, independent of the calendar density.
- **Address suggestions** — Whether the optional Photon address lookup is enabled; initially off.
- **Startup update check** — Whether to check for a newer release on launch; initially on.
- **Start with Windows** — Whether Windows starts Killendar minimized at sign-in; initially off.
- **Close to system tray** — Whether closing the main window hides it to the tray; initially off.
- **Export reminder** — Whether to show the export confirmation reminder.
- **Data folder** — The catalog folder, initially the Windows roaming profile’s Killendar folder.
