# Integration design

## Systems
- Finance system (posting awards/disbursements)
- Identity provider (SSO/MFA)
- Document management (storage, retention, compliance)
- Analytics platform (enterprise reporting)

## Patterns
- API-led connectivity via middleware (MuleSoft/API gateway)
  - System APIs: finance, docs, identity
  - Process APIs: grant lifecycle orchestration
  - Experience APIs: Salesforce-specific contracts

## Sync vs async
- Sync: validations, lookups, small transactions
- Async: award status changes, finance posting, large updates
  - Platform Events / CDC option (event-driven)
- Batch: nightly reconciliation, large reference datasets

## Reliability
- Idempotency keys (Application ID/Award ID)
- Retries with backoff in middleware
- Dead-letter/error queue concept
- Correlation IDs for tracing

## Sequence diagram
See `docs/diagrams/sequence-award-to-finance.*`