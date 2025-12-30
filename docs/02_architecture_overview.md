# Architecture overview

## High-level design
This solution models the grants lifecycle in Salesforce with three layers:
1) Experience layer: internal staff console and optional external applicant portal
2) Application layer: objects, flows, and validation rules for lifecycle automation
3) Integration layer: middleware/API gateway for finance, identity, and document management

```mermaid
flowchart LR
  U[Users\n- Program staff\n- Reviewers\n- Finance ops] --> SF[Salesforce org\nGrants management app]

  subgraph SF[Salesforce org]
    OBJ[Data layer\nCustom objects + Account/Contact]
    AUT[Automation\nRecord-triggered flows\nValidation rules]
    REP[Reporting\nReports + dashboards]
    OBJ --> AUT
    AUT --> REP
  end

  SF -->|API calls / events| INT[Integration layer\nMuleSoft or API gateway]

  INT --> FIN[Finance system\nPosting + reconciliation]
  INT --> DOC[Document management\nStorage/retention]
  INT --> IDP[Identity provider\nSSO/MFA]
  INT --> ANA[Analytics platform\nEnterprise reporting]
```

## Components
- Core data: Grant program, Grant, Application, Review, Award, Disbursement, Compliance artifact
- Operations: Case management for applicant questions (optional add-on)
- Automation: Flows for submit and approve-award, plus validation rules for guardrails
- Reporting: pipeline and funding KPIs

## Non-functional goals
- Security: least privilege access, record sharing, field-level security
- Reliability: idempotent automation patterns, clear error handling model
- Maintainability: prefer Flow where possible, Apex only for complex cases
- Scalability: avoid heavy synchronous processing, use async for heavy workloads

## Data Model
```mermaid
flowchart TB
  ACCT[Account\nApplicant organization]
  CONT[Contact\nApplicant contact]

  GP[GrantProgram__c]
  G[Grant__c]
  APP[Application__c]
  REV[Review__c]
  AWD[Award__c]
  DISB[Disbursement__c]
  CA[ComplianceArtifact__c]

  GP -->|1..many| G
  G -->|1..many| APP
  ACCT -->|1..many| APP
  CONT -->|1..many| APP

  APP -->|1..many| REV
  APP -->|0..1| AWD
  AWD -->|1..many| DISB
  APP -->|0..many| CA
```

## Sequence Diagram
```mermaid
sequenceDiagram
  participant Staff as Program staff
  participant SF as Salesforce
  participant Flow as Flow: Approve Award
  participant INT as Middleware/API gateway
  participant FIN as Finance system

  Staff->>SF: Update Application status = Approved
  SF->>Flow: Trigger record-triggered flow
  Flow->>SF: Query existing Award by ApplicationId
  alt Award exists
    Flow->>SF: No-op (idempotent)
  else No award
    Flow->>SF: Create Award (amount, status=Approved)
    Flow->>INT: Send Award payload (API/event)
    INT->>FIN: Post award
    FIN-->>INT: Return financeReferenceId
    INT-->>SF: Callback/update financeReferenceId
  end
```

