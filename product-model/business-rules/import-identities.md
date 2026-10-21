---
appliesTo:
- type: entity
  id: appointment
- type: entity
  id: repeating-series
references:
- kind: code
  role: implementation
  target: Services/IcsService.cs#IdFromUid
- kind: code
  role: implementation
  target: Services/CsvService.cs#StableId
- kind: code
  role: implementation
  target: Services/EventStore.Categories.cs#ImportEvents
---

# Import preserves existing entries with matching identities

Ordinary and series ICS entries use their source UID as identity; a non-GUID UID is mapped consistently. CSV identity is derived from title, start, end and location. Matching existing identities are skipped rather than overwritten; altered description or categories alone do not make a CSV row new.
