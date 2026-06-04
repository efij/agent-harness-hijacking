# LinkedIn Launch Post

🚨 New research: Agent Harness Hijacking

Claude Code dynamic workflows are a huge productivity leap.

But from a security perspective, they change the model from:

“AI coding assistant”

to:

“multi-agent developer automation runtime.”

That matters.

Because a workflow can now:

- spawn subagents
- read files
- run tools
- analyze repos
- use MCP/connectors
- modify code
- influence CI/CD
- burn tokens
- persist rules
- synthesize executive decisions

The risk is not just hallucination.

The real risk is:

👉 a useful workflow.js downloaded from GitHub
👉 that performs a real task
👉 while quietly expanding scope, harvesting context, burning tokens, biasing conclusions, or touching sensitive systems

I call this:

# Agent Harness Hijacking

Key concepts in the research:

1. Workflow Supply-Chain Attack
Downloaded workflows should be treated like executable automation, not prompt templates.

2. Token Farming
Like cryptomining abuse, but the stolen resource is LLM tokens, agent runtime, API quotas, and security review capacity.

3. Context Harvesting
A “market research” workflow may quietly collect roadmap, pricing, CRM, Slack, Jira, architecture, or security context.

4. Output Steering
A workflow can bias vendor selection, risk acceptance, architecture, or procurement while appearing objective.

5. Workflow Laundering
The final report looks clean, but the risky behavior happened in intermediate agent/tool steps.

Enterprise bottom line:

Do not run downloaded workflow.js files directly on enterprise repos, sensitive data, developer machines, or MCP-connected environments.

Approve only workflows that are:

✅ reviewed
✅ pinned
✅ sandboxed
✅ logged
✅ budgeted
✅ source-restricted
✅ MCP-allowlisted
✅ human-reviewed for sensitive actions

The key rule:

Untrusted content may inform analysis.
Untrusted content must never authorize action.

GitHub research: https://github.com/efij/agent-harness-hijacking
