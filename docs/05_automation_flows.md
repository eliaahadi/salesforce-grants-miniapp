# Automation flows

## Flow 1: Submit application (Record-triggered)
**Trigger:** Application__c created/updated when Status__c = Submitted  
**Actions:**
- If SubmittedDate__c is blank, set it to TODAY()
- Create initial Review__c record (optional)
- Create internal Task for analyst queue (optional)

**Guardrails:**
- Validation: RequestedAmount__c required when Submitted
- Validation: SubmittedDate__c required when Submitted

## Flow 2: Approve award (Record-triggered)
**Trigger:** Application__c updated when Status__c = Approved  
**Actions:**
- Get existing Award__c for this Application (idempotency)
- If none exists, create Award__c with AwardAmount__c (default from requested)
- Optionally update Application__c Status__c to Awarded

**Idempotency approach:**
- Prevent duplicate awards by checking for existing Award__c tied to Application__c

## Screenshots
- `docs/diagrams/screenshots/flow_submit_application.png`
- `docs/diagrams/screenshots/flow_approve_award.png`