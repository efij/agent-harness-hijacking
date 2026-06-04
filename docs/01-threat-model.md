# Threat Model: Claude Code Dynamic Workflows

## 1. Introduction

Claude Code dynamic workflows allow Claude to dynamically create task-specific orchestration logic, decompose tasks, run subagents, verify outputs, and perform large-scale work inside Claude Code.

This creates a new enterprise security model.

Traditional AI assistant risk:

```text
User asks question → model answers
```

Dynamic workflow risk:

```text
User asks task
  ↓
Claude creates harness / workflow logic
  ↓
Workflow spawns subagents
  ↓
Agents read files, docs, tickets, webpages, or tool outputs
  ↓
Agents may call shell, filesystem, browser, git, MCP, or SaaS connectors
  ↓
Workflow synthesizes results
  ↓
Workflow may modify files, influence decisions, or persist reusable behavior
```

## 2. Security framing

Dynamic workflows should be treated as privileged automation, not as simple prompts.

They can influence:

- source code
- developer machines
- CI/CD files
- package scripts
- cloud/IaC configuration
- internal documentation
- Slack/Jira/Confluence context
- MCP/connector actions
- security review outputs
- procurement decisions
- risk acceptance documents

## 3. Primary threat

The primary threat is not hallucination.

The primary threat is:

> Untrusted content influences a privileged workflow.

Examples of untrusted content:

| Source | Why it is risky |
|---|---|
| README files | Can contain hidden instructions |
| GitHub issues | User-controlled text |
| Pull requests | External contributor influence |
| Code comments | May be attacker-controlled |
| Package metadata | Supply-chain vector |
| Webpages | Prompt-injection surface |
| Slack messages | Internal user-generated content |
| Jira tickets | Business workflow injection surface |
| MCP responses | Tool output may become instruction |
| Downloaded workflow.js | Executable automation from unknown source |

## 4. Assets at risk

| Asset | Risk |
|---|---|
| Source code | IP exposure, unsafe modifications |
| Secrets | API keys, cloud credentials, tokens |
| CI/CD | Gate weakening, secret leakage, release bypass |
| Developer workstation | Local creds, shell access, cached sessions |
| MCP/connectors | Business-system data or actions |
| Internal docs | Strategy, architecture, customer data |
| Security findings | Known weaknesses and compensating controls |
| Workflow memory/rules | Persistent unsafe behavior |
| Token budget | Token farming and resource abuse |

## 5. Trust boundaries

| Boundary | Trust level | Handling |
|---|---:|---|
| User explicit request | Medium | Validate scope |
| Enterprise policy | High | Managed, centrally enforced |
| Repo files | Low | Treat as untrusted input |
| External webpages | Very low | Treat as hostile content |
| MCP output | Low | Treat as data, not instruction |
| Workflow.js from GitHub | Very low | Review like executable code |
| CLAUDE.md / project instructions | Medium-risk | Review and restrict |
| Shell commands | High-risk | Ask/deny controls |
| CI/CD changes | Critical | Human approval |
| Secrets/config | Critical | Deny by default |

## 6. Abuse chain

```text
Downloaded workflow.js
  ↓
Claims to perform useful task
  ↓
Developer runs it with broad permissions
  ↓
Workflow expands scope
  ↓
Subagents read repo/internal docs/MCP outputs
  ↓
Workflow burns tokens, collects context, biases output, or touches sensitive files
  ↓
Final report hides intermediate behavior
```

## 7. Enterprise risk statement

Claude Code dynamic workflows are enterprise-safe only when:

- workflow source is trusted
- execution is sandboxed
- permissions are centrally managed
- sensitive files are denied
- MCP/connectors are allowlisted
- token/tool/runtime budgets exist
- telemetry captures all actions
- sensitive changes require human approval
