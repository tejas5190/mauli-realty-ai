# n8n workflow lifecycle

## States
1. **Specified** — purpose, trigger, inputs, outputs, owner and risk documented.
2. **Built** — workflow JSON exists and has been reviewed.
3. **Imported** — imported into n8n but inactive.
4. **Tested** — positive, negative, edge, retry and error-path tests pass.
5. **Approved** — owner signs off on data access and external effects.
6. **Active** — enabled with monitoring and rollback plan.

A Git commit or successful import does not mean a workflow is tested or active.

## Required metadata
Document workflow name/version, purpose, trigger, credentials by display name only, input/output schema, data classification, external side effects, idempotency, retry behavior, test cases, approval owner, and rollback.

## Release rules
- Keep workflows inactive until tested and approved.
- Use synthetic records first.
- Verify invalid inputs cannot reach AI or external action nodes.
- Verify retries do not create duplicate leads, posts, or messages.
- Export a backup before modifying an active workflow.
- Never commit credential-bearing exports.
