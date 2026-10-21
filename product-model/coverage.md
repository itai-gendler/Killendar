---
scope: The desktop calendar, appointment and recurrence flows, exchange formats, local calendar files,
  categories, date preferences, core About behavior and supported command-line operations.
method: Read-only static tracing of entry points, UI handlers, services, persistence, bundled documentation
  and selected tests at the pinned upstream revision.
covered:
- description: Appointment editing, generated recurrence, replacements, category definitions and local
    persistence.
  paths:
  - Models/
  - Features/Appointments/
  - Services/Recurrence.cs
  - Services/EventStore.cs
  - Services/EventStore.Persistence.cs
  - Services/EventStore.Queries.cs
  - Services/EventStore.Categories.cs
  - Services/EventStore.Schema.cs
  - Services/CalendarDateSpan.cs
- description: Calendar browsing, selected-day agenda, repeat controls, category assignment, lookup and
    map actions.
  paths:
  - Features/Calendar/
  - Views/
  - Shell/CalendarHost.cs
  - Shell/DayAgendaPanel.cs
  - Shell/AppointmentView.cs
  - Shell/RepeatPanel.cs
  - Shell/Categories.cs
  - Shell/LocationLookup.cs
  - Shell/LocationMap.cs
- description: Calendar exchange parsing and export projections.
  paths:
  - Services/IcsService.cs
  - Services/CsvService.cs
  - Services/EmlService.cs
  - Services/HtmlExport.cs
- description: Calendar-file catalog, password and data-folder lifecycle.
  paths:
  - Features/Security/
  - Services/EventStore.Catalog.cs
  - Services/EventStore.Encryption.cs
  - Shell/SecurityHost.cs
  - Controls/KillendarsDialog.xaml.cs
  - Controls/PasswordDialog.xaml.cs
- description: Category manager and saved category color meaning.
  paths:
  - Controls/CategoriesDialog.xaml.cs
  - Services/CategoryManager.cs
- description: Language, date, browsing-span, density and shortcut behavior.
  paths:
  - Services/LocaleManager.cs
  - Services/DateFormatManager.cs
  - Services/WeekStartManager.cs
  - Shell/Language.cs
  - Shell/Density.cs
  - Shell/WorkWeek.cs
  - Shell/Shortcuts.cs
  - Shell/ShortcutsOverlay.cs
  - Controls/LanguageMenu.cs
  - Controls/DateSettingsMenu.cs
  - Settings.cs
- description: About, update, startup, tray, install and uninstall behavior.
  paths:
  - Features/About/
  - Services/UpdateService.cs
  - Services/StartupRegistration.cs
  - Services/CodeSignature.cs
  - App.Installation.cs
  - App.xaml.cs
  - Shell/Install.cs
  - Shell/About.cs
  - Shell/CloseToTray.cs
- description: Public agenda and creation command contracts and their desktop dispatch.
  paths:
  - Killendar.Cli/
  - Services/CalendarCommands.cs
  - Services/CommandLineEntry.cs
  - Shell/MainWindow.xaml.cs
exclusions:
- description: Build, packaging, CI, vendored native dependencies and automated test machinery are implementation
    support.
  paths:
  - build/
  - .github/
  - third_party/
  - Killendar.Tests/
  - tests/
  - choco/
  - Properties/
- description: Fonts, palettes, illustration assets and website styling are design rather than behavioral
    contracts.
  paths:
  - Fonts/
  - Themes/
  - Resources/
  - docs/
  - killendar-landing/kd.css
- description: Window chrome, animation, scaling, layout placement and presentation-only options are design
    details.
  paths:
  - Controls/Anim.cs
  - Controls/AccentShadow.cs
  - Controls/DwmChrome.cs
  - Shell/Chrome.cs
  - Shell/AppScale.cs
  - Shell/SidebarDock.cs
  - Shell/SidebarResize.cs
  - Shell/SidebarSlide.cs
  - Shell/ToolbarOverflow.cs
  - Shell/ToolbarStyle.cs
  - Shell/ThemeFlyout.cs
  - Shell/RailOrder.cs
  - Services/ThemeManager.cs
  - Services/FilmGrain.cs
unmapped:
- description: Public marketing website and store listing interactions are peripheral to the local calendar
    workflows.
  paths:
  - killendar-landing/
  - store/
- description: Generic file picker navigation, pinned places and folder-tree management are peripheral
    shared controls.
  paths:
  - Controls/FileDialog.xaml.cs
  - Controls/FileDialog.Browser.cs
  - Controls/FileDialog.Navigation.cs
  - Controls/FileDialog.Places.cs
  - Controls/FileDialog.PinOrder.cs
  - Controls/FileDialog.Interaction.cs
  - Controls/FileDialog.Filters.cs
  - Controls/FolderTree.cs
- description: Color picker eyedropper and reusable swatch-slot lifecycle are peripheral to category color
    assignment.
  paths:
  - Controls/ColorPickerDialog.cs
- description: Legacy JSON migration is a compatibility path outside current calendar authoring workflows.
  paths:
  - Services/EventStore.Migration.cs
- description: Demo calendar generation is a demonstration mode rather than normal appointment authoring.
  paths:
  - Services/DemoData.cs
- description: Package-manager exit-code mapping is peripheral deployment maintenance.
  paths:
  - Services/InstallerExitCodes.cs
- description: Whole-series edits made after single-date edits exist, and the series editor opened on a
    series as a whole rather than from one of its dates.
  paths:
  - Services/EventStore.Persistence.cs
  - Features/Appointments/AppointmentEditor.cs
- description: Crash-log and diagnostic collection behavior is outside the selected user workflows.
  paths:
  - CrashLog.cs
  - Controls/AccessibilityAudit.cs
limitations: []
---

# Coverage


