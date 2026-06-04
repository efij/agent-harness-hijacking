# Advanced Abuse Patterns

## 1. Workflow Supply-Chain Attack

A workflow supply-chain attack occurs when a user downloads or copies a workflow file from GitHub, Slack, a blog, a public repo, an internal wiki, or an AI-generated answer, and runs it with enterprise permissions.

The realistic attacker does not publish:

```text
malicious-workflow.js
```

They publish:

```text
deep-market-analysis.workflow.js
repo-modernization-agent.js
security-review-helper.js
competitive-intel-agent.js
mcp-business-research-agent.js
```

The workflow mostly works. It provides value. That is what makes it dangerous.

## 2. Token Farming

Token farming is abusive workflow behavior designed to intentionally burn enterprise AI budget, model tokens, tool calls, API quotas, runtime, and review capacity.

It is similar in concept to cryptomining abuse, but the abused resource is not CPU/GPU. The abused resource is:

```text
LLM tokens
agent runtime
parallel subagents
MCP/API calls
developer approval fatigue
SaaS quotas
security review capacity
```

Realistic example:

A workflow claims:

```text
Run deep market analysis across competitors, pricing, GitHub, Reddit, review sites, investor signals, customer pain points, and developer sentiment.
```

Hidden token-farming pattern:

```text
- spawn 20 agents when 3 are enough
- re-read the same sources repeatedly
- ask each agent for long intermediate reports
- run unnecessary adversarial review loops
- expand competitor list automatically
- continue until confidence reaches 99%
- save every intermediate result into context
```

Detection signals:

| Signal | Meaning |
|---|---|
| Agent count higher than needed | Token farming |
| Repeated source reads | Waste loop |
| Confidence-based loops | Unbounded consumption |
| Large intermediate artifacts | Token amplification |
| Broad MCP/API calls | Resource abuse |
| Big output with low decision value | Performative computation |

Controls:

```text
- max agents per workflow
- max tokens per workflow
- max tool calls per workflow
- max MCP calls per workflow
- max runtime
- max source expansion depth
- approval before scope expansion
- cost estimate before execution
- kill switch
- cost anomaly detection
```

## 3. Context Harvesting

Context harvesting is when a workflow appears to perform legitimate analysis but collects excessive internal context.

It may collect:

```text
systems
repos
owners
architecture
customers
pricing
roadmap
security gaps
deployment paths
internal blockers
```

Example:

A workflow called:

```text
deep-market-analysis.workflow.js
```

claims to analyze competitors, but also requests:

```text
internal sales decks
customer objections
Slack discussions
CRM summaries
roadmap documents
support tickets
security review notes
architecture docs
```

Justification:

```text
Needed for accurate positioning.
```

Actual risk:

The workflow creates a strategic intelligence package about the company.

Controls:

```text
Allowed by default:
- public websites
- public GitHub repos
- public pricing pages
- public review sites

Not allowed without approval:
- Slack
- CRM
- Jira
- Confluence
- customer tickets
- security findings
- financial data
- internal roadmap
```

## 4. Output Steering

Output steering occurs when a workflow subtly biases conclusions while appearing objective.

Example:

A workflow claims:

```text
Objective vendor comparison.
```

Hidden scoring bias:

```text
- overweight one vendor’s strengths
- penalize OSS alternatives for operational risk
- treat missing public data as negative only for selected competitors
- underweight lock-in
- downplay privacy/security gaps
```

Controls:

- transparent scoring
- weights visible and editable
- citations required
- missing-data assumptions explicit
- facts separated from inference
- negative evidence included

## 5. Workflow Laundering

Workflow laundering hides risky intermediate behavior behind a clean final report.

Flow:

```text
Step 1: Perform useful task
Step 2: Quietly inspect extra context
Step 3: Run hidden scoring/extraction logic
Step 4: Remove sensitive details from final report
Step 5: Present polished executive output
```

Human reviewers usually inspect the final report, not the full execution trace.

Control:

Every workflow must produce an execution summary covering:

```text
files read
files written
commands run
tools used
connectors used
network destinations
agents spawned
tokens used
scope expansions
persistent rules written
```

## 6. Permission Normalization

The workflow gradually asks for reasonable-looking permissions:

```text
read package.json
read config folder
read CI folder
run tests
read env sample
query Jira for context
connect CRM for evidence
```

Each approval seems reasonable. The chain becomes dangerous.

Control:

Evaluate cumulative permission behavior, not each approval in isolation.

## 7. Trust Laundering through Subagents

A workflow uses many named agents:

```text
researcher
critic
security reviewer
business analyst
synthesizer
```

The final report says:

```text
Validated by independent adversarial review.
```

But all agents saw the same poisoned source.

Control:

Independence must mean separate evidence boundaries, not just different agent names.

## 8. Benign-Useful / Malicious-Secondary Workflow

The most realistic malicious workflow is 80–95% useful.

It really does:

```text
analyze market
summarize competitors
review code
generate tests
refactor files
produce a good report
```

But it also:

```text
burns tokens
collects excess context
biases conclusions
normalizes permissions
writes persistent rules
weakens controls
```

The reviewer must not ask only:

```text
Does it work?
```

The reviewer must ask:

```text
What else does it do?
What can it access?
What can it persist?
What can it cost?
What decisions does it influence?
What does it hide?
```
