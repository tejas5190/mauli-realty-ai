# Agent specifications

Agents are bounded assistants invoked by workflows. They do not receive unrestricted access to every business system.

## Property Intelligence Agent
Purpose: turn owner-supplied property information into a structured, reviewable listing draft.

Allowed: normalize text, identify missing fields and contradictions, draft copy from supplied facts, propose owner questions.

Forbidden: invent amenities, prices, areas, approvals, RERA details, possession dates, availability or returns; publish content; contact leads; bypass validation.

Output: structured JSON with source facts, missing information, claims requiring verification, draft copy, and `needs_human_review`.

## Market Research Agent
Summarize public market information with source and retrieval date. Distinguish asking prices from transaction prices. Never claim estimates are verified transactions or coverage is exhaustive without evidence.

## Content Agent
Create platform-specific drafts and creative briefs from approved property facts and approved media. Never fabricate project visuals, alter material facts, publish, or use unlicensed assets.

## Lead Qualification Agent
Classify enquiries and suggest next actions using approved criteria. Do not infer sensitive traits, make discriminatory decisions, message without consent/approval, or mark a booking confirmed without authoritative confirmation.
