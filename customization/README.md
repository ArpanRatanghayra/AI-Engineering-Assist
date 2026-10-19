# Project Customization Guide

## Purpose

Adapt the development-assistance workflows to a repository without creating a parallel SDLC. The project profile records local engineering facts and links to the project's existing PR, approval, CI/CD, release, security, and operational procedures.

The framework may prepare evidence for those procedures. It does not define or enforce them.

## Baseline versus project extensions

The shared baseline stops at developer/lead analysis, requested local implementation, local validation, technical-readiness findings, and project-process handoff. Adopt that baseline first.

A project may add an assistance workflow when its architecture, risk, tooling, or repeated delivery needs justify one. Record each extension in the project profile with:

- the problem it solves and paths or change types it covers;
- its accountable project owner;
- required inputs and expected output;
- commands, tools, access, and permission boundaries;
- how it hands work to existing project procedures;
- pilot evidence and criteria for keeping, changing, or removing it.

Project extensions do not automatically become part of the common framework. Do not add speculative workflows “for completeness.”

## Project overlay

Use existing repository conventions where possible. A typical setup is:

```text
AGENTS.md                    # concise assistant entry point
.ai/project-engineering-assist.md  # project profile, or an existing docs location
.ai/sop/                     # only focused engineering guidance the project needs
CLAUDE.md                    # optional thin adapter
.cursor/rules/               # optional thin adapter
```

Do not copy central guidance or enterprise policy into the project. Link to canonical sources and record only actionable local facts.

## What the profile should contain

- Services, owners, criticality, data classification, languages, and frameworks.
- Repository layout and canonical architecture, API, operational, and standards documentation.
- Local build, format, lint, test, security-scan, and validation commands.
- Risk triggers that change the depth of analysis or require the developer to consult a project process.
- Focused engineering guidance for relevant paths or change types.
- Links to existing PR, reviewer, approval, CI/CD, deployment, and exception procedures.
- Known gaps or missing documentation.
- Project-specific assistance extensions, when justified, and their ownership/boundaries.

## Focused change guidance

Add a local SOP only when it helps a developer plan or implement a recurring high-risk change. Examples include:

| Scope | Useful engineering guidance |
| --- | --- |
| API/event/schema | Compatibility, consumer impact, contract tests, documentation |
| Database/migration | Data classification, migration and rollback analysis, performance validation |
| Infrastructure/IAM | Least privilege, plan validation, cost/security impact, state boundary |
| AI/LLM | Model/prompt evaluation, grounding and data boundaries, safety, cost, latency |
| Regulated data | Minimization, redaction, retention, approved test-data handling |

The SOP should point to the project's formal reviewer, approval, or release procedure instead of restating it.

## Adoption sequence

1. Create a project profile from the [template](../templates/project-engineering-assist-profile.md).
2. Verify local commands and canonical documentation with project maintainers.
3. Add only the two or three highest-value change-type guides.
4. Add thin tool adapters referencing the profile.
5. Pilot with real developer work and measure time, useful findings, false alarms, and missing context.
6. Remove guidance that does not improve a decision, implementation, validation, or handoff.

Project owners may separately add or change CI, branch protection, CODEOWNERS, permissions, and release controls through their normal governance process. That work is outside this framework.
