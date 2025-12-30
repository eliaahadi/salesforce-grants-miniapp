# Reporting and metrics

## Dashboards
1) Applications by Status (count + sum requested)
2) Awards by Status (count + sum awarded)
3) Average Days to Decision (SubmittedDate__c -> DecisionDate__c)

## Metrics definitions
- Pipeline volume: count of applications by stage
- Funding requested: sum(RequestedAmount__c)
- Funding awarded: sum(AwardAmount__c)
- Time to decision: DecisionDate__c - SubmittedDate__c
- SLA proxy: cases opened vs resolved (if using Case)

## Screenshots
- `docs/diagrams/screenshots/dashboard_pipeline.png`