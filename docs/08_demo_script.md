# 3-minute demo script

## 0:00–0:30 Context
"This is a grants lifecycle mini app designed to show enterprise patterns: a clear data model, lifecycle automation, reporting, and governance."

## 0:30–1:15 Data model
- Show Grant program, Grant, Application related list
- Explain why Review and Disbursement use master-detail (rollups/reporting)

## 1:15–2:15 Automation
- Open an Application in Draft
- Change Status to Submitted
- Show SubmittedDate updated and Review created (Flow 1)
- Change Status to Approved
- Show Award created and linked (Flow 2)
- Mention idempotency check to prevent duplicates

## 2:15–2:45 Reporting
- Open dashboard: pipeline + dollars requested vs awarded

## 2:45–3:00 Enterprise wrap
- Security model (least privilege, record sharing)
- Integration design (API-led via middleware, events/batch patterns)
- Next enhancements (portal, cases, audit evidence, CI/CD)