# Approval Matrix

| Use case | Decision | Required controls |
|---|---:|---|
| Public-source-only research | Allow | Browser/source allowlist, budget |
| Read-only code explanation | Allow | No shell, no secrets |
| Test generation | Allow | Sandbox, diff review |
| Low-risk refactoring | Allow | Sandbox, PR review |
| Security review | Conditional | Read-only first, no secrets |
| Market research using internal docs | Conditional | Data owner approval |
| Slack/Jira analysis | Conditional | Scoped project/channel only |
| MCP read-only connector | Conditional | Owner, scope, audit |
| MCP write connector | High risk | Formal risk acceptance |
| CI/CD modification | High risk | CODEOWNERS + security/platform approval |
| IaC modification | High risk | Cloud/security approval |
| Production data analysis | Usually reject | Use approved data platform |
| Autonomous deployment | Reject by default | Exception only |
| Downloaded GitHub workflow.js | Reject by default | Review/sandbox/registry required |
| Skipped permissions | Reject | Only disposable lab |

## Approval logic

```text
If workflow processes untrusted input + accesses sensitive data + can change state,
then reject or redesign.

If workflow needs MCP/connectors, require formal risk acceptance.

If workflow modifies CI/CD, IAM, auth, payment, customer-data, or production-related files,
require human approval.

If workflow source is unknown, run only in isolated review environment.
```
