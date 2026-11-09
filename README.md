# Mauli Enterprises — AI Marketing Operating System

Cloud-first, modular marketing operations for Mauli Enterprises.

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
- GitHub: source code, documentation, prompts, workflow specifications and version history.
- n8n Cloud: default engine for deterministic automation, integrations, schedules, webhooks and approval gates.
- Sim: candidate engine for AI-agent workflows, research synthesis, knowledge-assisted drafting and tool-using agents. Evaluating via a proof of concept; not yet deployed or connected.
- Managed database: canonical structured properties, campaigns, leads and approvals.
- Managed object storage: media and private documents.
- AI APIs: extraction, drafting, classification and analysis.
- Meta/WhatsApp APIs: only after permissions, policy and billing checks.

See [Architecture](docs/ARCHITECTURE.md), [Sim and n8n decision](docs/SIM-AND-N8N.md), [Security](docs/SECURITY.md), and [Workflow lifecycle](docs/WORKFLOW-LIFECYCLE.md).

## Status
Foundation and platform evaluation stage. Files in this repository are specifications/templates unless explicitly marked deployed and tested. Committing a workflow does not deploy or activate it.

## Repository map
- `docs/` architecture, security, platform decisions and operating procedures
- `agents/` agent roles and guardrails
- `workflows/` automation specifications and sanitized workflow exports
- `schemas/` shared data contracts
- `prompts/` versioned prompt templates
- `config/` safe example configuration
