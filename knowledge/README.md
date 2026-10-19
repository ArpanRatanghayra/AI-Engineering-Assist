# Repository Knowledge Model

## Goal

Store the minimum durable context needed for a person or AI agent to understand a service and safely begin a change without repeating broad discovery on every task.

Knowledge is version-controlled with the service where practical. It is not a replacement for source code, active configuration, approved operational systems, or human judgement. Each material statement should link to evidence and show when it was last verified.

## Canonical artifact types

| Artifact | Purpose | Update trigger |
| --- | --- | --- |
| Service profile | Purpose, owner, boundaries, architecture, local setup, operations, and known gaps for one service. | New service, material service change, ownership/operational change, or discovery finding |
| Dependency record | Explicit upstream/downstream relationship, contract, failure effect, owner, and verification evidence. | API/event/schema/data/deployment dependency change |
| Standards profile | Applicable engineering standards plus verified local conventions and known conflicts. | Framework/build/CI/policy/pattern change or newly discovered convention |
| Decision record (ADR) | A durable, approved architecture or design choice and its consequences. | Material design decision or changed decision |
| Runbook | Operator procedure for a recurring operational task, incident, deployment, verification, or rollback activity. | Operational behavior or support process change |
| Change record | Time-bound proposal, implementation plan, validation evidence, and release considerations. | A non-trivial change; archive or link after completion |

## Suggested placement

Use existing repository documentation structure when it already has a canonical home. For a service without one, use this layout near the service root:

```text
docs/
  service-profile.md
  architecture.md
  dependencies.md
  standards.md
  decisions/
    ADR-0001-<short-title>.md
  runbooks/
  changes/
```

Do not create a parallel documentation tree merely because this framework exists. The knowledge steward must first identify the repository's existing documentation convention.

## Required metadata

Every generated or materially refreshed knowledge artifact should include:

```md
Status: Draft | Verified | Needs review | Superseded
Last verified: YYYY-MM-DD
Verified against: <source paths, links, or approved system records>
Owner: <team or role, if known>
```

For information that cannot be verified, use `Status: Needs review`; never imply verification.

## Content rules

- Record facts and their evidence; explicitly label inference, proposal, conflict, and unknown.
- Prefer links and concise summaries over duplicated configuration, long code excerpts, or copied policy text.
- Separate **current state** from **proposed change** and from **historical decisions**.
- Update the affected artifact in the same change as the code/configuration whenever feasible.
- Keep security-sensitive implementation detail at the approved level of disclosure. Never document secret values or sensitive customer/member information.
- When a source of truth lives outside the repository, document the approved reference and owner rather than copying volatile content.

## Freshness model

The agent should use repository knowledge first, then verify only the parts relevant to the new task. It must refresh the artifact when:

- the task changes a fact documented there;
- the artifact is marked `Needs review` or `Superseded`;
- its cited evidence no longer exists or conflicts with current source;
- the task touches a high-risk boundary and the relevant information has no credible verification date.

This reduces repeated context gathering without allowing stale summaries to become trusted facts.
