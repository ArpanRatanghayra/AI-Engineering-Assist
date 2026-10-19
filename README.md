# AI Engineering Assist

> A risk-proportionate AI companion for developers and technical leads.

## Executive summary

| Question | Answer |
| --- | --- |
| What problem does this address? | AI-assisted development can begin with incomplete context, inconsistent tool behavior, hidden assumptions, and weak handoff evidence. |
| Who is it for? | Developers and technical leads using approved AI assistants on non-trivial software changes. |
| What does it provide? | A tool-neutral, risk-proportionate set of prompts, workflows, and templates for understanding a service, clarifying a change, planning and implementing requested local work, validating it, and preparing a technical handoff. |
| What is the intended value? | Faster context gathering, fewer missed dependencies and risks, more consistent local validation, and clearer evidence for the project's established delivery process. |
| What does it not provide? | PR governance, organizational approvals, CI/CD, deployment, production control, compliance enforcement, or release decisions. |
| Who remains accountable? | Developers and technical leads remain responsible for the engineering work; project and organizational authorities retain their existing review, approval, security, release, and production responsibilities. |
| What is its current maturity? | A working baseline and pilot-ready prompt/workflow library. It is not yet a proven platform or an organization-wide mandated standard. |

## Purpose

Provide a consistent way for AI assistants to support engineering work without replacing developer judgement or the project's existing SDLC. The framework ends with an evidence-backed developer/lead handoff.

## Scope

This framework assists with engineering work before and around the project's formal delivery process. It provides analysis, implementation support, technical review prompts, and handoff evidence.

The following remain outside this framework and are defined by each project's existing structure:

- pull-request creation, review policy, CODEOWNERS, and merge decisions;
- approval roles, approval records, change management, and risk acceptance;
- CI/CD design, required checks, artifact promotion, and release gates;
- deployment, environment access, production verification, incident response, and rollback authority;
- enterprise security, privacy, compliance, and audit controls.

A project profile may link to these processes so the assistant can prepare the right evidence. It must not redefine, duplicate, bypass, or claim to enforce them.

## Operating assumptions

This baseline assumes:

- a developer or technical lead owns the request and reviews AI-produced analysis and changes;
- the repository and relevant project documentation are accessible to the user and assistant;
- the project already owns, or will separately define, its PR, approval, CI/CD, security, deployment, and release processes;
- assistants receive least-privilege access and do not gain authority merely because a workflow mentions an action;
- source code, configuration, tests, approved records, and project systems remain authoritative over generated summaries;
- missing, stale, or conflicting information is reported rather than guessed;
- workflow depth is proportional to impact, likelihood, blast radius, reversibility, exposure, and existing controls;
- teams will pilot and adapt the baseline before treating it as standard practice.

If an assumption is not true for a project, record it as a gap in the project profile rather than silently compensating for it.

## Baseline and extension model

The current common baseline ends at an evidence-backed developer or technical-lead handoff. It includes context discovery, requirements and risk clarification, design support, implementation planning, requested local implementation, local validation, technical-readiness review, and durable knowledge updates.

Projects may add further assistance when a demonstrated need and project design justify it. Examples could include project-specific test orchestration, repository-native commands, specialized security or architecture prompts, or read-only delivery-system integrations. Such extensions must:

- live in the project profile or a focused project-owned extension;
- state their owner, scope, inputs, outputs, permissions, and safety boundary;
- reuse the common evidence and risk principles without changing the baseline for every project;
- link to authoritative project procedures instead of redefining approvals, PR policy, CI/CD, deployment, or release governance;
- be piloted and measured before becoming a wider recommendation.

An optional extension is not part of the current baseline merely because it is described or proposed. Moving a capability into the shared baseline requires an explicit design decision and evidence that it is broadly useful.

## Principles

1. Inspect the relevant service, instructions, and evidence before editing.
2. Separate confirmed facts, inferences, assumptions, conflicts, and unknowns.
3. Match process depth to change risk; do not produce an artifact that has no decision or evidence value.
4. Design material boundary changes before implementation.
5. Treat tests, documentation, observability, rollout, and rollback as part of the change.
6. Report what was run, what passed or failed, and what was not run.
7. Hand work back to the project's existing PR, approval, CI/CD, and release processes.

All workflows use the [shared preflight instruction](instructions/preflight.md) for evidence and safety rules. Stage documents should not repeat those rules.

## Lifecycle

```text
Discover when context is missing
  -> Define requirements and risk
  -> Resolve design decisions when required
  -> Plan the change and its validation
  -> Implement when the developer requests local changes
  -> Perform a technical readiness review
  -> Prepare the project-specific handoff
  -> Retain durable knowledge
```

This is routing, not a requirement to create every artifact for every change.

| Change level | Typical characteristics | Minimum path |
| --- | --- | --- |
| Trivial | Text-only or mechanical change with no behavior, contract, security, data, operational, or infrastructure impact | Follow repository instructions; make and validate the focused change |
| Low | Small, isolated behavior change with limited blast radius and easy rollback | Concise requirements/plan, focused tests, documentation check |
| Moderate | Service behavior or operational change with meaningful failure modes | Requirements/risk, implementation plan, local validation, technical readiness review |
| High | Contract, consumer, shared component, sensitive data, security boundary, migration, or cross-service impact | Design support, compatibility strategy, rollout/rollback analysis, and identification of project-required reviewers |
| Critical | Material availability risk, destructive migration, production IAM/infrastructure, or regulated-data boundary change | Analysis and planning only until the project's required authorities permit implementation |

Risk is based on impact, likelihood, blast radius, reversibility, exposure, and the strength of existing controls—not file type alone. A project profile may make this matrix stricter or more specific.

## Workflow map

Use only the workflows needed for the current stage.

| Need | Workflow | Output |
| --- | --- | --- |
| Service purpose, ownership, architecture, dependencies, or operations are unclear | [Service Context Discovery](agents/service-context-discovery.md) | Source-linked context brief and gaps |
| Applicable standards and local patterns are unclear | [Standards and Pattern Discovery](agents/standards-and-pattern-discovery.md) | Change-specific conformance checklist |
| The request needs scope, acceptance criteria, or risk classification | [Requirements and Risk](agents/requirements-and-risk.md) | Requirements and risk brief |
| A material design decision or boundary may change | [Design Readiness](agents/design-readiness.md) | Decision to proceed, constrain, or create a design/ADR |
| The change is understood but not yet implementation-ready | [Implementation Planning](agents/implementation-planning.md) | Ordered, evidence-backed plan |
| A ready plan is requested for local implementation | [Requested Local Implementation](agents/requested-local-implementation.md) | Code, tests, documentation, validation, and handoff |
| Implemented work needs a developer/lead readiness assessment | [Change Review](agents/change-review.md) | Technical findings and project-handoff notes; not formal PR approval |
| A project explicitly requests supported environment checks | [Environment Validation](agents/environment-validation.md) | Optional observations under the project's own runbook and authority |
| Verified facts should survive the current task | [Repository Knowledge Steward](agents/repository-knowledge-steward.md) | Updated canonical project documentation |
| A repository is adopting this model | [Project Customization](agents/project-customization.md) | Project profile linking existing procedures and constraints |

Output structures live in [templates](templates/README.md). Durable service documentation follows the [repository knowledge model](knowledge/README.md).

## Handoff to the project SDLC

The AI may discover, analyze, draft, implement requested local work, run allowed local validation, and report evidence. Developers and technical leads use that output within their project's established SDLC.

The project or organization remains responsible for:

- business scope and acceptance of requirements;
- material design trade-offs and policy exceptions;
- risk acceptance and security/privacy decisions;
- formal PR review and merge;
- required CI checks and release gates;
- deployment, migration, cloud/data/state mutation, and production decisions.

Missing knowledge is an output, not permission to guess. Generated summaries help navigation; cited code, configuration, approved records, CI results, and operational systems remain authoritative.

## Project adoption

Each adopting repository needs a small project profile containing its owners, service classification, standard local commands, risk triggers, canonical documentation, and links to its existing PR, CI/CD, approval, and release procedures. Use the [customization guide](customization/README.md) and [project profile template](templates/project-engineering-assist-profile.md).

Thin adapters for Codex, Claude, Cursor, and Copilot are in the [integration kit](integration/README.md). Adapters guide development assistance; project tooling and controls remain authoritative.

Adopt it through a measured pilot and remove process that does not affect a decision, control, or reusable fact. The customization guide owns the detailed adoption sequence.

Start with the current baseline. Add project extensions only after the baseline exposes a concrete gap; record them in the project profile so contributors can distinguish shared behavior from local additions.

Planned platform capabilities are tracked in [TODO.md](TODO.md).

## Completion

The framework's work is complete when the developer or lead has an evidence-backed implementation and a clear handoff containing validation performed, limitations, risks, and project-specific next steps. The project's existing SDLC—not this framework—determines when the change is approved, merged, released, or complete.
