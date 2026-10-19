# Workflows

These files are tool-neutral workflow specifications, not autonomous services. An assistant may load the relevant file as a prompt or expose it through a native skill or command.

Route work by need; do not run every workflow mechanically:

- Use context and standards discovery only when the relevant facts are missing or stale.
- Use requirements/risk before planning a behavior change.
- Use design readiness when a material boundary or decision may change.
- Use implementation planning before non-trivial implementation.
- Use requested local implementation and technical-readiness review when the developer reaches those stages; environment validation is an optional project extension.
- Use project customization during repository adoption and knowledge stewardship whenever durable facts change.

All workflows inherit the evidence and safety rules in the [shared preflight instruction](../instructions/preflight.md). They do not grant approval or authority.
