# Tool Integration Kit

Install this kit after creating a [Project Engineering Assist Profile](../templates/project-engineering-assist-profile.md). It gives developers and leads short assistance commands while the project's existing SDLC remains authoritative.

## Installation

1. Copy the relevant files from `adapters/` to the project root or native tool location.
2. Replace `<PROJECT_PROFILE>` with the project profile's repository-relative path.
3. Copy `commands/` to the native command location when supported:
   - Cursor: `.cursor/commands/`
   - Copilot: use the command text in a prompt file or approved custom-agent workflow
   - Codex/Claude: invoke the matching command file explicitly or use the `ai-engineering-change` skill
4. Link the profile to existing PR, approval, CI/CD, and release procedures. Do not reproduce those procedures in an adapter.

## Adapter principle

Every adapter must remain short. It loads the project profile and the applicable workflow; it must not duplicate the charter or invent project-specific rules.

## Supported workflow commands

| Command | Outcome |
| --- | --- |
| `/ai-discover` | Service context and standards evidence before a change |
| `/ai-plan` | Requirements, risk, design readiness, and implementation plan |
| `/ai-implement` | Requested local implementation with tests/docs/validation |
| `/ai-review` | Developer/lead technical-readiness findings before project review |
| `/ai-validate-env` | Optional project-authorized environment observations |

## Project-process boundary

These adapters do not create PR policy, approvals, CI checks, release gates, or permissions. The project profile links to those existing processes only so the assistant can prepare an appropriate handoff.
