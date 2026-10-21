---
singleton: true
references:
- kind: code
  role: implementation
  target: App.Installation.cs
- kind: code
  role: implementation
  target: Features/About/AboutController.cs
- kind: code
  role: implementation
  target: Services/UpdateService.cs
---

# Installation

The local copy of Killendar and the release information shown for it.

## Information kept

- **Scope** — Portable, current-user installation, all-users installation, or removed.
- **Version** — The running or installed release version.
- **Release date** — The running release date.
- **Publisher** — The verified publisher or unsigned status.
- **Certificate thumbprint** — The certificate thumbprint presented in About.
- **Executable hash** — The calculated SHA-256 of the running executable.
- **Signature valid** — Whether the running executable has a valid signature.
- **Available version** — The newer release found by a successful update check.

## States

### Portable

A local copy that has not been installed.

### Installed

A copy installed for the current user or all users.

### Removed

The installed copy has been removed.
