# Shared Preflight Instruction

Use this instruction before planning, implementing, reviewing, or releasing a change.

## Objective

Establish sufficient, evidence-backed context to make a safe next-step recommendation. This is a discovery activity, not authorization to edit files, create remote artifacts, deploy, or change cloud/data state.

## Required behavior

1. Read the nearest repository and directory-level instructions before inspecting or proposing changes.
2. Identify the request, intended outcome, scope, non-goals, and acceptance criteria. Distinguish explicit facts from assumptions.
3. Locate evidence for service purpose, architecture, owners, dependencies, data/security classification, design and coding standards, framework patterns, dependency injection/configuration conventions, tests, operations, and release controls.
4. Prefer source code, version-controlled configuration, approved architecture records, runbooks, and current CI definitions over stale summaries. Cite the source path or approved system record for every material assertion.
5. Record unavailable, inconsistent, or unverified information as a knowledge gap. Do not infer approval, ownership, data classification, compatibility, or production behavior from naming alone.
6. Identify whether the request may affect a public/internal API, event/schema, data store, data classification, IAM/secrets, infrastructure, deployment, consumers, monitoring, rollback, or established framework/component patterns.
7. Recommend the next required SDLC step and list the human decision or approval needed, if any.

## Safety boundary

During preflight, do not:

- edit code, configuration, state, or documentation unless the user separately asks for an update;
- execute deployments, infrastructure applies, migrations, state changes, destructive commands, or production actions;
- disclose secrets, credentials, protected/member data, sensitive logs, or state-file contents;
- claim a validation, approval, design decision, or service owner exists without evidence.

## Minimum output format

```md
# <Workflow name>: <service or change>

## Request understood
## Evidence reviewed
## Confirmed context
## Assumptions and knowledge gaps
## Affected boundaries and preliminary risk signals
## Recommended next step
## Human decisions or approvals needed
```
