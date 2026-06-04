# Workflow Review Checklist

Before allowing any dynamic workflow:

```text
1. Who authored it?
2. Where was it downloaded from?
3. Is the source trusted?
4. Is the version pinned?
5. Is the hash recorded?
6. What files can it read?
7. What files can it write?
8. Can it run shell commands?
9. Can it access network?
10. Can it call MCP/connectors?
11. Can it access Slack/Jira/Confluence/CRM?
12. Can it modify CI/CD or package scripts?
13. Can it write persistent instructions?
14. Does it have token/tool/runtime limits?
15. Does it ask before expanding scope?
16. Does it expose all intermediate actions?
17. Does it separate public and internal data?
18. Does it have a business owner?
19. Does it have a security owner?
20. Does it have logs suitable for IR?
21. What is the rollback/removal process?
22. Can it influence procurement or risk decisions?
23. Does it include hidden scoring weights?
24. Does it process sensitive data?
25. Is there a kill switch?
```

## Reject immediately if

```text
- unknown GitHub source
- requires skipped permissions
- accesses secrets
- uses arbitrary MCP
- modifies CI/CD
- writes persistent rules
- hides intermediate actions
- has no token budget
- expands scope without approval
```
