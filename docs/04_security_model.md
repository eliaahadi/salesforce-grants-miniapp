# Security model (talk track)

## Design principles
- Least privilege by default
- Minimize profiles; use permission sets/groups for access
- Conservative record visibility (OWD) for sensitive objects
- Field-level security for PII/sensitive fields
- Auditability: track key field history and approval actions

## Personas
- Applicant (external simulation): view only their own applications
- Program analyst: view/update assigned program applications
- Program manager: approve awards; view broader scope

## Controls
- Object access: permission set groups enable CRUD for each persona
- Record access: OWD + sharing rules + (optional) role hierarchy
- Field access: FLS restricts sensitive fields (PII, risk flags, finance IDs)
- Governance: periodic access reviews and change control for production

## Validation + audit
- Validation rules enforce required fields on state changes
- Field history tracking for status, amounts, and decision fields