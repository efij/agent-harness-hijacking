# MCP / Connector Review Checklist

## Ownership

```text
1. Who is the business owner?
2. Who is the system owner?
3. Who approves the data access?
4. Who monitors usage?
5. Who can revoke access?
```

## Access

```text
1. Exact MCP server name
2. Exact connector URL/source
3. Exact OAuth scopes
4. Read/write capability
5. Data classes exposed
6. User group allowed
7. Tenant/environment allowed
8. Rate limits
9. Audit availability
10. Retention and logging
```

## Workflow-specific risks

```text
1. Can workflow call connector automatically?
2. Can workflow request broader scopes?
3. Can workflow export data locally?
4. Can workflow mix connector data with public data?
5. Can workflow write back to the system?
6. Can workflow trigger business actions?
7. Can workflow persist connector outputs?
```

## Minimum decision

```text
Read-only MCP:
Conditional approval with owner, scope, audit, and data classification.

Write MCP:
High-risk approval only with human-in-the-loop and risk acceptance.

Unknown MCP:
Reject.
```
