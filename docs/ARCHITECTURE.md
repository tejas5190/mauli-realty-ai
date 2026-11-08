# Architecture

## Operating model
Cloud-first. The user's PC is an optional browser client—not a server, worker, database, or required development host.

## Components
| Component | Responsibility | Authority |
|---|---|---|
| GitHub | Source, docs, prompts, sanitized workflow specifications/exports | Source of truth for code |
| n8n Cloud | Deterministic orchestration, schedules, webhooks, API calls, routing and approval gates | Default automation engine |
| Sim (evaluation) | Agent-centric workflows, research synthesis, knowledge-assisted drafting and tool use | Candidate agent execution layer; not canonical data |
| Managed relational DB | Properties, leads, campaigns, approvals, audit records | Canonical operational data |
| Managed object storage | Property photos, creative assets, private documents | Media source |
| AI APIs | Extraction, drafting, classification, analysis | Never authoritative for property facts |
| Meta/WhatsApp | Approved publishing and communication | External platform records |

## Platform strategy
Use n8n Cloud as the default for deterministic business automation. Evaluate Sim for workflows where agent reasoning, tool use, knowledge retrieval or agent observability materially helps. Do not replace n8n until a measured proof of concept passes the criteria in [Sim and n8n decision](SIM-AND-N8N.md).

Sim is not yet deployed or connected. Sim Cloud is the preferred first evaluation path to avoid requiring a local PC runtime. Self-hosting requires a separate managed infrastructure decision.

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
Free tiers have quotas and can change. Do not assume AI APIs, Sim, n8n, WhatsApp, Meta advertising, databases, or storage are unlimited or permanently free.
