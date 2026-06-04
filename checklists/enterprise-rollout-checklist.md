# Enterprise Rollout Checklist

## Phase 1 — Policy

```text
- Define approved use cases
- Define rejected use cases
- Define sensitive repositories
- Define sensitive data classes
- Define MCP approval flow
- Define workflow registry ownership
```

## Phase 2 — Technical baseline

```text
- Managed settings
- Deny secret paths
- Ask/deny shell policy
- Sandbox/dev container
- MCP allowlist
- Network restrictions
- Token/tool/runtime budgets
- Logging and telemetry
```

## Phase 3 — Workflow governance

```text
- Internal workflow registry
- Version pinning
- Static review
- Security owner
- Business owner
- Expiration/re-review
- Approval matrix
```

## Phase 4 — Detection

```text
- Token anomalies
- Tool-call anomalies
- Secret path attempts
- MCP scope expansion
- CI/CD file changes
- Persistent rule writes
- Unknown network destinations
```

## Phase 5 — Red team validation

```text
- prompt injection tests
- poisoned README tests
- poisoned MCP output tests
- token-farming tests
- context-harvesting tests
- output-steering tests
- workflow-laundering tests
```
