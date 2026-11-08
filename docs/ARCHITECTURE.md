# Architecture

## Operating model
Cloud-first. The user's PC is an optional browser client—not a server, worker, database, or required development host.

## Components
| Component | Responsibility | Authority |
|---|---|---|
| GitHub | Source, docs, prompts, sanitized workflow exports | Source of truth for code |
| n8n Cloud | Orchestration, schedules, API calls, routing | Executes approved workflows |
| Managed relational DB | Properties, leads, campaigns, approvals, audit records | Operational data source |
| Managed object storage | Property photos, creative assets, documents | Media source |
| AI APIs | Extraction, drafting, classification, analysis | Never authoritative for property facts |
| Meta/WhatsApp | Approved publishing and communication | External platform records |

## Modular workflows
- WF-01 Property Intake & Intelligence
- WF-02 Market Research
- WF-03 Content & Creative Factory
- WF-04 Approval & Publishing
- WF-05 Lead Intake & Qualification
- WF-06 WhatsApp Follow-up
- WF-07 Campaign Reporting

These are planned modules, not claims of deployment.

Use stable identifiers: `company_id`, `property_id`, `campaign_id`, `lead_id`, `approval_id`.

## Human approval required
- Public posts and scheduled content
- Bulk or first-contact promotional messaging
- Advertising budget, bid, or targeting changes
- Legal, regulatory, price, availability, and project-status claims
- Marking a lead booked or property sold

## Reliability requirements
Every workflow needs input validation, idempotency for retryable actions, explicit error paths, bounded retries/backoff, correlation IDs, structured logs without secrets, and alerting. Test with synthetic data before production.

## Cost discipline
Free tiers have quotas and can change. Do not assume AI APIs, WhatsApp, Meta advertising, databases, or storage are unlimited or permanently free.
