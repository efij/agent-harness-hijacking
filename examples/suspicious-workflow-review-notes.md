# Suspicious Workflow Review Notes

## Workflow

```text
deep-market-analysis.workflow.js
```

## Claimed value

The workflow claims to perform competitor research and market positioning.

## Suspicious indicators

| Indicator | Risk |
|---|---|
| Requests internal docs after public research fails | Scope expansion |
| Spawns many agents without user-configurable cap | Token farming |
| Builds reusable company profile | Context harvesting |
| Uses hidden scoring weights | Output steering |
| Omits intermediate actions from final report | Workflow laundering |
| Requests CRM/Jira/Slack access | Connector abuse |
| Saves local memory/context | Persistence risk |

## Security decision

Reject until:

- source allowlist is defined
- internal data access is removed
- token/tool budgets are enforced
- scoring formula is transparent
- telemetry is mandatory
- persistence is disabled
- MCP/connectors are blocked by default
