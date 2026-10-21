---
kind: primary
routes:
  main: Desktop
steps:
- text: Open the application information.
  kind: actor
  entities: []
  contexts:
    main:
      place: desktop::about
  actor: user
- text: Show the Installation version, release date, publisher, certificate thumbprint and executable
    hash.
  kind: product
  entities:
  - entity: installation
    effect: reads
    facts:
    - Version
    - Release date
    - Publisher
    - Certificate thumbprint
    - Executable hash
  contexts:
    main:
      place: desktop::about
  actor: user
references:
- kind: code
  role: implementation
  target: Features/About/AboutController.cs
- kind: code
  role: implementation
  target: Services/CodeSignature.cs
---

# View About

## Trigger

The User opens About.

## Outcome

About shows the running version and release date, the publisher, the certificate thumbprint, and the SHA-256 of the running executable. An unsigned copy is shown as not signed.
