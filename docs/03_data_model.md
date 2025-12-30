# Data model

## Objects
- Account (Applicant organization)
- Contact (Applicant contact)
- GrantProgram__c (program)
- Grant__c (funding opportunity)
- Application__c (application submission)
- Review__c (evaluation)
- Award__c (award decision)
- Disbursement__c (payments/reimbursements)
- ComplianceArtifact__c (documents/audit artifacts)

## Relationships
- Grant__c -> (Lookup) GrantProgram__c
- Application__c -> (Lookup) Grant__c
- Application__c -> (Lookup) Account, Contact
- Review__c -> (Master-Detail) Application__c
- Award__c -> (Lookup) Application__c
- Disbursement__c -> (Master-Detail) Award__c
- ComplianceArtifact__c -> (Lookup) Application__c

## Key fields (examples)
### Application__c
- Status__c (Draft, Submitted, Under review, Approved, Rejected, Awarded, Closed)
- RequestedAmount__c (Currency)
- SubmittedDate__c (Date)
- DecisionDate__c (Date)
- RiskScore__c (Number 0-100)

### Award__c
- Status__c (Draft, Approved, Sent to finance, Funded, Closed)
- AwardAmount__c (Currency)
- FinanceReferenceId__c (Text)

## Diagram
See `docs/diagrams/data-model.*`