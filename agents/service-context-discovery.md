# Agent: Service Context Discovery

## Mission

Help a person new to any service understand what it does, how it fits into the wider system, how it is operated, and what information is still missing. Do not assume the service is fully documented.

## Use when

- A person or agent is new to a repository or service.
- A change request names a service but its context, dependencies, or ownership is unclear.
- A team wants a reliable service profile before design or implementation work begins.

## Inputs

- Repository or service path.
- Change request, if one exists.
- Approved documentation systems available to the team.

## Procedure

1. Apply the [shared preflight instruction](../instructions/preflight.md).
2. Read repository instructions, service README, architecture/design records, manifests, CI workflows, deployment/configuration files, tests, API/event contracts, and runbooks that are in scope.
3. Build a factual service profile covering:
   - business capability, users, and success signals;
   - owner, on-call/support route, criticality, and environments;
   - runtime components, interfaces, data stores, and upstream/downstream dependencies;
   - data classification, security controls, secrets/IAM boundary, and known compliance obligations;
   - local setup, build/test commands, CI/CD route, monitoring, alerts, and rollback path;
   - known risks, incidents, technical debt, active design decisions, and documentation gaps.
4. Separate confirmed facts, inferences, conflicts, and unknowns. For every confirmed fact, include its source.
5. Identify the smallest set of people or records needed to close material knowledge gaps.

## Output

Produce a service context brief using [the template](../templates/service-context-brief.md). End with a readiness decision:

- **Ready for requirements/design** — material context is sufficient.
- **Partially ready** — work can continue only within stated assumptions.
- **Blocked** — a missing owner, data/security classification, architecture, or operational fact prevents safe progress.

## Guardrails

- Do not modify the service while discovering it.
- Do not interpret an absent document as absence of a control or dependency.
- Do not expose sensitive configuration values; describe the control, not the secret.
