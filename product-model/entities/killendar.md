---
relations:
- entity: appointment
  verb: contains
  cardinality: one-to-many
- entity: repeating-series
  verb: contains
  cardinality: one-to-many
- entity: single-date-edit
  verb: contains
  cardinality: one-to-many
- entity: category
  verb: contains
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: Services/EventStore.cs
- kind: code
  role: implementation
  target: Services/EventStore.Catalog.cs
- kind: code
  role: implementation
  target: Features/Security/SecurityController.cs
domain: killendars
---

# Killendar

A calendar kept as one local `.kcal` file, with its own appointments, category definitions and optional password. The User can keep as many as they like.

## Information kept

- **Name** — The calendar file name.
- **File location** — Where the calendar file is kept.
- **Size** — Its file size as shown in Manage Killendars.
- **Last changed** — The file modification time.
- **Password protection** — Whether a password protects this calendar.
- **Session access** — Whether this calendar is open for use, closed, or awaiting unlock.
- **Active** — Whether this is the selected calendar.

## States

### Plaintext

A Killendar without a password: an ordinary SQLite file anyone with the file can read.

### Encrypted

A Killendar with a password, encrypted at rest; its contents open only with that password.
