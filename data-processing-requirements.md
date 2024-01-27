# Data Processing Requirements Document

This document outlines entity-specific transformations and processing steps required for each entity in the Global Alliance Bank SBDL using Kafka project.

## Account Entity

### ContractIdentifier

- **Operation:** INSERT
- **OldValue:** NULL
- **NewValue:** Account ID

### SourceSystemIdentifier

- **Operation:** INSERT
- **OldValue:** NULL
- **NewValue:** System Identifier (e.g., BDL)

...

### PartyRelations

- **Operation:** INSERT
- **OldValue:** NULL
- **NewValue:** Array of Party Relations, each having:
  - PartyIdentifier
  - PartyRelationshipType
  - PartyRelationStartDateTime
  - PartyAddress
    - AddressLine1
    - AddressLine2
    - AddressCity
    - AddressPostalCode
    - AddressCountry
    - AddressStartDate

