# Security and privacy

This repository is public. Assume every committed file is visible to anyone.

## Never commit
- API keys, OAuth tokens, refresh tokens, passwords, private keys, webhook secrets
- n8n credential exports or credential values
- Customer names, phone numbers, email addresses, chat transcripts, lead exports
- Owner identity documents, signatures, bank details, private contracts
- Non-public property documents, access codes, private links
- Production database dumps or unredacted logs

## Credentials
Use the relevant cloud provider's credential manager or secret store. Reference credential names in documentation, never secret values in source code, prompts, workflow JSON, issues, or logs.

If a secret is committed: revoke/rotate it immediately, inspect usage/access logs, remove it from the current tree, and assess Git history cleanup. Deleting the current file does not erase historical copies.

## Personal data
Collect only data needed for a defined business purpose. Restrict access, define retention, and honor consent and opt-out requirements. Use synthetic or redacted data in tests and examples.

## Property advertising
Verify all property facts against owner-supplied records and authoritative sources. A human must check MahaRERA registration, applicable QR code, approvals, project status, area definitions, price inclusions and availability. AI output is a draft, not legal verification.

## External actions
Require explicit human approval before public publishing, outbound promotional messaging, and ad spend changes. Record approver, approved content/action, and timestamp.
