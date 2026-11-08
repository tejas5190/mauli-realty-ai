# Sim and n8n: orchestration decision

## Decision
Add Sim as an approved candidate platform for AI-agent workflows. Do not remove n8n Cloud or migrate workflows yet.

Use a hybrid evaluation:
- **n8n Cloud** remains the default for deterministic business automation, schedules, webhooks, API integrations, retries, routing, and operational workflows.
- **Sim** is evaluated for agent-centric workflows: multi-step reasoning, tool-using agents, knowledge retrieval, workflow-as-agent tools, and agent run observability.
- Both platforms must call the same governed APIs/data services. Neither platform becomes the source of truth for property or lead records.

## Why not replace n8n immediately?
The platforms overlap, but a full replacement would create migration risk before a real workflow has been built and tested. Sim's current product includes visual workflows, agents, integrations, tables, files, knowledge, logs, API deployment and MCP. n8n remains a strong general-purpose integration and event-automation engine.

## Recommended responsibility split
| Workload | Preferred first choice | Reason |
|---|---|---|
| Property form intake and field validation | n8n | Deterministic trigger and validation |
| Duplicate checks and database writes | n8n / database constraints | Predictable data operations |
| Research synthesis across sources | Sim candidate | Agent reasoning and tool use |
| Listing copy draft from verified facts | Sim candidate | Structured agent drafting |
| Creative brief generation | Sim candidate | Multi-step content reasoning |
| Approval request and publishing gate | n8n + human approval | Explicit deterministic gate |
| Lead webhook capture and deduplication | n8n | Reliable event processing |
| Lead intent summary and suggested response | Sim candidate | Bounded AI assistance |
| WhatsApp outbound messaging | n8n after consent/approval | Auditable external side effect |
| Scheduled KPI aggregation and reports | n8n / database | Repeatable scheduled processing |

## Integration pattern
1. Keep canonical records in the managed relational database and media in managed object storage.
2. Trigger a Sim workflow from n8n through a documented API, or expose a deployed Sim workflow as an API/MCP tool where appropriate.
3. Pass only the minimum required fields and stable IDs; avoid copying full customer records into agent prompts.
4. Sim returns structured output with source references, confidence/uncertainty, missing facts and proposed actions.
5. Validate the output against a schema before storing it.
6. Require a human approval record before public publishing, promotional messaging, budget changes, or property-status changes.
7. Log correlation IDs, platform run IDs, latency, model/provider, and cost without logging secrets or unnecessary personal data.

Do not allow an agent to directly publish, message leads, change ad spend, or mark a property booked/sold.

## Deployment choice
Prefer Sim Cloud for the first proof of concept if its current plan, data handling, integrations and pricing meet requirements. This avoids requiring a local PC runtime or maintaining our own server.

Self-hosted Sim is a separate infrastructure project. Current upstream guidance requires Node.js 20+, Docker and Docker Compose for the setup wizard; production operation also requires managed persistence, secrets, backups, updates, monitoring and a publicly reachable secure endpoint if remote MCP clients must connect. Do not attempt self-hosting on the user's PC.

## Proof-of-concept acceptance tests
Build one isolated workflow: **Property Listing Draft Assistant**.
- Input: synthetic property record with a stable `property_id`.
- Agent may use only supplied facts and approved reference material.
- Output: strict JSON containing draft copy, source facts, missing information, contradictions, claims needing verification, owner questions, and `needs_human_review`.
- Test missing fields, conflicting prices/areas, prompt injection in descriptions, unsupported claims, malformed output, timeouts and retries.
- Verify it cannot publish, message, or change the canonical property record.
- Compare output quality, execution reliability, latency, cost, integration effort and auditability against an equivalent n8n + LLM API workflow.

## Go/no-go rule
Keep Sim only if the proof of concept materially improves agent quality or maintainability without weakening security, approval controls, reliability or total cost. Do not migrate the rest of the automation stack based on feature claims alone.

## Upstream references
- [Sim GitHub repository](https://github.com/simstudioai/sim)
- [Sim self-hosting documentation](https://docs.sim.ai/platform/self-hosting)
- [Sim MCP documentation](https://docs.sim.ai/mcp/overview)
- [Sim introduction](https://docs.sim.ai/introduction)
