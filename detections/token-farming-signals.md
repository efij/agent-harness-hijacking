# Token Farming Signals

## Definition

Token farming is abusive workflow behavior designed to burn enterprise AI tokens, agent runtime, MCP/API quotas, and review capacity while appearing to perform legitimate deep work.

## Signals

| Signal | Description |
|---|---|
| Excessive agents | More agents than task complexity requires |
| Repeated source reads | Same source processed repeatedly |
| Confidence loops | Runs until arbitrary confidence score improves |
| Long intermediate reports | Huge outputs not needed for decision |
| Broad scope expansion | Adds competitors, repos, docs, channels, tickets |
| MCP/API overuse | Heavy connector usage for low-value task |
| No budget | No max token/tool/runtime cap |
| Low decision density | Large output with little actionable value |

## Example suspicious prompt pattern

```text
Continue researching until confidence is above 99%.
Use as many independent agents as needed.
Expand source coverage automatically.
Generate full intermediate reports for each agent.
```

## Controls

```text
- max agents
- max tokens
- max runtime
- max tool calls
- cost estimate before run
- approval for scope expansion
- workflow-level anomaly detection
- per-user budget monitoring
```
