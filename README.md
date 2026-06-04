# Agent Harness Hijacking

## OWASP-style security research for Claude Code Dynamic Workflows

**Agent Harness Hijacking** is a practical security research project focused on the risks created by dynamic multi-agent workflows in Claude Code and similar developer automation systems.

Dynamic workflows change the security model from “AI coding assistant” to “multi-agent developer automation runtime.”

## Core thesis

The main risk is not that Claude may hallucinate.

The main risk is:

> An untrusted instruction, hidden inside code, docs, tickets, Slack, webpages, package metadata, MCP output, or a downloaded workflow file, may influence a privileged multi-agent workflow that can read files, run tools, modify code, call connectors, burn tokens, or steer business decisions.

## Why this matters

Dynamic workflows are not just prompt templates.

They are closer to:

- GitHub Actions
- CI/CD scripts
- VS Code extensions
- developer automation tools
- MCP servers
- agentic workflow runtimes
- executable supply-chain artifacts

A workflow downloaded from GitHub may appear useful, produce real business value, and still contain secondary malicious or abusive behavior.

## Key concepts introduced

| Concept | Meaning |
|---|---|
| Agent Harness Hijacking | Manipulation of dynamic workflow orchestration, subagents, tools, or final synthesis. |
| Workflow Supply-Chain Attack | Abuse of copied/downloaded workflow files, shared skills, agent configs, hooks, or reusable automation. |
| Token Farming | Malicious or abusive workflow behavior designed to burn enterprise AI tokens, tool quotas, runtime, and review capacity. |
| Context Harvesting | Excessive collection of business, product, customer, security, or architecture context under a legitimate task. |
| Output Steering | Hidden biasing of workflow scoring, vendor selection, risk decisions, or strategic conclusions. |
| Workflow Laundering | Hiding risky intermediate behavior behind a clean final report. |
| Benign-Useful / Malicious-Secondary Workflow | A workflow that mostly works as advertised while quietly expanding scope, collecting context, wasting budget, or weakening controls. |

## Security verdict

For S&P500 and large enterprise environments:

```text
Do not allow downloaded workflow.js execution directly on enterprise repos, developer machines, internal docs, or MCP-connected systems.

Approve only reviewed, pinned, sandboxed, logged, budgeted, source-restricted workflows from an internal registry.
```

## Quick decision table

| Use case | Decision |
|---|---|
| Read-only code explanation | Allow |
| Public-source-only research | Allow |
| Test generation in sandbox | Allow |
| Low-risk refactoring with diff review | Allow |
| Security review with no secret access | Conditional |
| Internal docs / Slack / Jira analysis | Conditional |
| MCP / connector usage | High risk |
| CI/CD modification | High risk |
| Production data analysis | Usually reject |
| Autonomous deployment | Reject by default |
| Downloaded GitHub workflow.js | Reject unless reviewed and sandboxed |
| Skipped permissions on enterprise repo | Reject |

## The enterprise rule

Before running any dynamic workflow, the organization must be able to answer:

```text
1. What can the workflow access?
2. What can it change?
3. What can it call?
4. What can it persist?
5. What can it cost?
6. What decision can it influence?
7. What evidence proves it stayed in scope?
```

If the answer is unclear, reject.

## Documentation

- [Threat Model](docs/01-threat-model.md)
- [OWASP-style Top 10](docs/02-owasp-style-top-10.md)
- [Advanced Abuse Patterns](docs/03-advanced-abuse-patterns.md)
- [Enterprise Controls](docs/04-enterprise-controls.md)
- [Approval Matrix](docs/05-approval-matrix.md)
- [References](docs/06-references.md)

## Practical artifacts

- [Workflow Review Checklist](checklists/workflow-review-checklist.md)
- [MCP / Connector Review Checklist](checklists/mcp-connector-review-checklist.md)
- [Enterprise Rollout Checklist](checklists/enterprise-rollout-checklist.md)
- [Suspicious Workflow Signals](detections/suspicious-workflow-signals.md)
- [Token Farming Signals](detections/token-farming-signals.md)
- [Execution Summary Schema](examples/execution-summary.schema.json)
- [Claude Code Enterprise Settings Example](examples/claude-code-enterprise-settings.example.json)

## Disclaimer

This project provides defensive research, risk analysis, detection logic, and safe non-executable examples. It does not provide working exploit code, credential theft logic, bypass instructions, or malware.
