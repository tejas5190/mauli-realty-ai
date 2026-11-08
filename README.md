# Mauli Realty — AI Marketing Operating System

Cloud-first, modular marketing operations for Mauli Realty.

## Principles
- Cloud-first: the user's PC is not a required development host or runtime.
- Human approval before public posts, promotional messages, and ad-budget changes.
- Never invent property facts, approvals, amenities, measurements, prices, possession dates, or MahaRERA details.
- This is a public repository: never commit credentials, customer/lead data, owner documents, private property records, or unredacted logs.
- Keep workflows modular, testable, observable, and reversible.
- Optimize for qualified leads, site visits, conversions, and cost per qualified lead—not vanity metrics.

## Planned modules
1. Property intake and validation
2. Property intelligence and listing preparation
3. Market and competitor research
4. Content and creative production
5. Human approval and publishing
6. Lead capture, qualification, and CRM
7. Consent-aware WhatsApp follow-up
8. Campaign reporting

## Cloud architecture
- GitHub: source code, documentation, prompts, workflow exports, version history.
- n8n Cloud: orchestration, integrations, schedules, workflow execution.
- Managed database: structured properties, campaigns, leads, approvals.
- Managed object storage: media and documents.
- AI APIs: extraction, drafting, classification, analysis.
- Meta/WhatsApp APIs: only after permissions, policy and billing checks.

## Status
Foundation stage. Files in this repository are specifications/templates unless explicitly marked deployed and tested. Committing a workflow does not deploy or activate it.

## Repository map
- `docs/` architecture, security and operating procedures
- `agents/` agent roles and guardrails
- `workflows/` n8n workflow specifications and sanitized exports
- `schemas/` shared data contracts
- `prompts/` versioned prompt templates
- `config/` safe example configuration

See [Architecture](docs/ARCHITECTURE.md), [Security](docs/SECURITY.md), and [Workflow lifecycle](docs/WORKFLOW-LIFECYCLE.md).
