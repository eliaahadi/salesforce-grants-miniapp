# Salesforce grants management mini app (portfolio)

A lightweight Salesforce implementation that models a grants lifecycle end-to-end and demonstrates enterprise patterns:
- Data model for grants, applications, review, awards, disbursements, compliance artifacts
- Workflow automation using Salesforce Flow (submit application, approve award)
- Security model talk track (least privilege, record sharing, field security)
- Integration design patterns (API-led via middleware, event-driven option)
- Reporting dashboard for program KPIs

## Why this project
This mirrors common public-sector CRM/grants modernization needs:
- Structured lifecycle and audit trail
- Case management for applicant support
- Integrations to finance, identity, and document systems
- Governance and release discipline

## Quick start (demo)
1. Create sample records (Grant program → Grant → Applicant org/contact → Applications)
2. Update an application status to `Submitted` to trigger submit flow
3. Update an application status to `Approved` to trigger award creation flow
4. View dashboard for pipeline and dollars

## Artifacts
- Architecture overview: `docs/02_architecture_overview.md`
- Data model: `docs/03_data_model.md`
- Security: `docs/04_security_model.md`
- Flows: `docs/05_automation_flows.md`
- Integrations: `docs/06_integrations_design.md`
- Reporting: `docs/07_reporting_and_metrics.md`
- Demo script: `docs/08_demo_script.md`

## Tech
- Salesforce Lightning Experience
- Custom objects + standard objects (Account, Contact)
- Salesforce Flow (record-triggered)
- Reports and dashboards


# Applicant support console (Salesforce Service Cloud) — portfolio project

A Service Cloud console built to support high-volume applicant inquiries (eligibility, documentation, portal issues, application status).
Demonstrates enterprise patterns: triage, routing, SLA-oriented workflows, privacy controls, agent productivity tooling, reporting, and integration design.

## What’s included
- Case lifecycle and routing (queues + assignment rules; Omni-Channel optional)
- Data model and triage fields aligned to reporting and auditability
- Security model (least privilege, record access, field-level security)
- Agent productivity (case page layout, quick text/macros, suggested next steps)
- Reporting dashboard (backlog, time-to-resolution, top issue types, escalation rate)
- Integration design (API-led patterns to loan/grants system, docs, identity, analytics)
- Optional code: Apex Invocable triage + LWC Applicant 360 component

## Why this project
This mirrors applicant support workflows used in public-sector programs (e.g., farm loans / grants):
- consistent responses, audit trail, and controlled access to sensitive applicant info
- clear operational visibility (queues/backlog/SLA) and reliable escalation paths

## Demo steps (3 minutes)
1) Create a Case with Issue Type + Severity
2) Observe assignment to the correct queue
3) Move case through lifecycle statuses and capture resolution
4) Show dashboard metrics and trend view

## Artifacts
Start here: docs/02_architecture.md and docs/09_demo_script.md