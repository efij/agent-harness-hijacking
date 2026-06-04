# References

## Primary references

1. Anthropic — Claude Code subagents and dynamic workflows
   https://code.claude.com/docs/en/agent-sdk/subagents
   Subagents isolate context, run work in parallel, support tool restrictions, and are the operational surface behind dynamic workflow risk.

2. Anthropic — Claude Code permissions
   https://code.claude.com/docs/en/agent-sdk/permissions
   Claude Code permissions support hooks, deny rules, permission modes, allow rules, and runtime approval callbacks. Deny rules can block tools even when permissive modes are used.

3. Anthropic — Claude Code security
   https://code.claude.com/docs/en/security
   Claude Code uses permission-based controls, prompt-injection safeguards, network approval, trust verification, command-injection detection, and fail-closed matching.

4. OWASP Top 10 for Large Language Model Applications
   https://owasp.org/www-project-top-10-for-large-language-model-applications/
   Relevant categories include Prompt Injection, Sensitive Information Disclosure, Supply Chain, Excessive Agency, and Unbounded Consumption.

5. Anthropic — Claude Code auto mode
   https://code.claude.com/docs/en/auto-mode
   Anthropic describes permission automation, reinforcing the need for controlled permission models and audit boundaries.

## Research assumptions

This project focuses on defensive enterprise risk analysis. It does not claim that Claude Code dynamic workflows are malicious by design. The concern is that dynamic workflows create a new automation surface that requires governance, review, isolation, and telemetry.
