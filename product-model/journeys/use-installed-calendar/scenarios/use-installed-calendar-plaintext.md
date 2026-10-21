---
kind: primary
result: achieved
routes:
  main: Desktop
references:
- kind: code
  role: implementation
  target: App.Installation.cs#InstallAndRelaunch
- kind: code
  role: implementation
  target: App.xaml.cs#OnStartup
steps:
- capability: install-killendar
  text: Confirm installing the portable copy.
  kind: actor
  actor: user
  entities: []
  contexts:
    main:
      place: desktop::installation
- capability: install-killendar
  text: Change the Installation to installed and relaunch.
  kind: product
  actor: user
  entities:
  - entity: installation
    effect: changes
    from: Portable
    to: Installed
    facts:
    - Scope
  contexts:
    main:
      place: desktop::calendar
- capability: browse-calendar
  text: Inspect the calendar in the relaunched application.
  kind: actor
  actor: user
  entities: []
  contexts:
    main:
      place: desktop::calendar
- capability: browse-calendar
  text: Show appointments in the active period.
  kind: product
  actor: user
  entities:
  - entity: appointment
    effect: reads
    facts:
    - Title
    - Start
    - End
    - All day
    - Location
    - Description
    - Attendees
    - Categories
  contexts:
    main:
      place: desktop::calendar
---

# Install and continue in the installed copy

## Trigger

The User installs a portable copy whose active calendar is plaintext.

## Outcome

The installed application relaunches and the User reads the active calendar.
