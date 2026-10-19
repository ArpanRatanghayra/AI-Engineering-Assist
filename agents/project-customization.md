# Agent: Project Customization

## Mission

Create a concise overlay that maps the assistance workflows to a repository's services, risks, commands, owners, and existing SDLC references. Follow the [customization guide](../customization/README.md); do not create a parallel approval, PR, CI/CD, or release process.

## Inputs

- Applicable enterprise and repository policies.
- Repository architecture, tests, security tooling, local-development guidance, and links to project delivery procedures.
- Owners for engineering, architecture, security, operations, and release decisions.

## Procedure

1. Apply the [shared preflight instruction](../instructions/preflight.md).
2. Discover service boundaries, stack, data classification, criticality, commands, owners, dependencies, and canonical project documentation.
3. Identify the few path or change types that need requirements beyond the common baseline.
4. For each, define useful engineering analysis, local validation, and the existing project procedure to consult.
5. Distinguish assistant guidance from project-mandated requirements; link to the authoritative source for the latter.
6. Create or update the [project profile](../templates/project-engineering-assist-profile.md) and only the focused SOPs the project needs.
7. Record documentation gaps and the project owner or source that can resolve them.
8. Verify that a contributor can identify the affected path, risk, local commands, expected evidence, and project-specific next step without chat history.

## Output

A version-controlled project profile and focused engineering SOPs where justified, with links to existing project delivery processes.

## Guardrails

- Higher-precedence policy cannot be weakened or replaced by a project overlay.
- Do not define PR review, approval, CI/CD, release, or production procedures here.
- Link to canonical standards instead of copying them.
- Do not create rules that have no observed risk or decision value.
- Do not change CI, branch protection, CODEOWNERS, permissions, deployment, or access settings as part of this workflow.
