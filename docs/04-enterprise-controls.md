# Enterprise Controls for Dynamic Workflows

## 1. Default enterprise position

```text
Downloaded Claude workflow.js files are untrusted executable automation.

They must not be run directly on enterprise repos, developer machines, sensitive data, CI/CD systems, or MCP-connected environments.
```

## 2. Mandatory baseline

| Control | Requirement |
|---|---|
| Managed settings | Security-owned baseline |
| Permission policy | Deny / ask / allow rules |
| Sandboxing | Dev container, VM, or restricted environment |
| Secret deny rules | Sensitive paths denied by default |
| MCP allowlist | Approved servers only |
| Workflow review | Treat workflow as code |
| Version pinning | No unpinned external workflows |
| Telemetry | All actions logged |
| Budgets | Token/tool/runtime limits |
| Human review | Required for sensitive changes |

## 3. Sensitive file deny list

```text
.env
.env.*
*.pem
*.key
*.p12
*.pfx
id_rsa
id_ed25519
~/.ssh/*
~/.aws/*
~/.azure/*
~/.gcloud/*
~/.kube/config
.npmrc
.pypirc
docker-compose.override.yml
secrets.*
credentials.*
terraform.tfstate
terraform.tfvars
```

## 4. Sensitive commands

Require deny or explicit approval:

```text
environment dumping
credential discovery
recursive home-directory search
curl/wget to unknown destinations
package publishing
git push
cloud IAM mutation
kubectl against production
terraform apply
helm upgrade
database migration
CI/CD secret printing
file deletion
permission broadening
```

## 5. Sensitive repo areas

Require CODEOWNERS / platform / security review:

```text
.github/workflows/
.azure-pipelines/
Jenkinsfile
Dockerfile
docker-compose*
package.json scripts
lockfiles
Terraform
CloudFormation
CDK
Helm
Kubernetes manifests
IAM policies
auth code
payment code
PII/customer-data code
security controls
logging/audit code
```

## 6. MCP / connector controls

| Requirement | Description |
|---|---|
| Approved server only | No arbitrary local MCP |
| Read-only default | Write requires separate approval |
| Exact scopes | No broad OAuth |
| Owner approval | Business and system owner |
| Data classification | Know what data is exposed |
| Audit | Tool-level logging |
| Human-in-loop | Required for write/destructive actions |
| No scope escalation | Workflow cannot request more access mid-run without approval |

## 7. Runtime budgets

Minimum runtime constraints:

```text
max_agents: 5 by default
max_tokens: defined per workflow class
max_runtime_minutes: defined per workflow class
max_tool_calls: defined per tool
max_mcp_calls: defined per connector
max_scope_expansion_depth: 1
require_approval_for_scope_expansion: true
```

## 8. Workflow registry

Approved workflows must be stored in an internal registry with:

```text
workflow name
version
hash
owner
reviewer
approved use cases
allowed data sources
allowed tools
denied tools
token budget
MCP permissions
last review date
expiration date
change history
```

## 9. Logging requirements

Log:

```text
workflow file
workflow version
user
repo/project
start/end time
agents spawned
all subagent prompts
all files read
all files written
all shell commands
all MCP calls
all browser/network destinations
tokens estimated
scope expansions
persistent writes
policy violations
final output
```

## 10. Kill conditions

Terminate workflow if:

```text
- secret path is accessed
- unknown MCP server is used
- unknown network destination is called
- CI/CD file is modified without approval
- runtime/token budget exceeded
- workflow writes persistent rules
- workflow expands scope without approval
- workflow hides intermediate actions
```
