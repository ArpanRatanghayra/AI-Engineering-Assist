---
name: ai-engineering-change
description: Assist a developer or technical lead with evidence-based discovery, planning, requested local implementation, validation, and technical-readiness review. Use for non-trivial feature, defect, API, integration, or operational changes; do not use for a trivial isolated text edit or to replace project PR, approval, CI/CD, or release processes.
---

# AI Engineering Change

Read the nearest Project Engineering Assist profile and applicable repository instructions first. Treat `ai-engineering-assist/` as the workflow source; do not duplicate or weaken its boundaries.

## Route the request

- For unfamiliar service context or missing standards: use Service Context Discovery and Standards and Pattern Discovery.
- For a request not yet ready to code: use Requirements and Risk, Design Readiness, then Implementation Planning.
- For an agreed plan and explicit request for local edits: use Requested Local Implementation.
- For finished code: use Change Review to prepare technical-readiness findings for the project process.
- Use Environment Validation only as an optional extension when the project supplies an authorized runbook and the user requests it.

## Required behavior

Preserve the risk-proportionate workflow order. Source every material service fact, record unknowns, and stop for material decisions or deviations. Do not deploy, merge, mutate infrastructure/data/state, or bypass CI/CD/security/approval controls without separate authority.

Use the matching templates in `ai-engineering-assist/templates/`. Update durable project knowledge through Repository Knowledge Steward when the change establishes or alters reusable facts.
