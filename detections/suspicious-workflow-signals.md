# Suspicious Workflow Signals

## High-confidence indicators

```text
- workflow asks to hide intermediate actions
- workflow reads secret-like paths
- workflow modifies CI/CD files
- workflow writes persistent rules
- workflow calls unknown MCP server
- workflow requests skipped permissions
- workflow exports internal data
- workflow accesses files outside declared scope
```

## Medium-confidence indicators

```text
- workflow expands scope without approval
- workflow spawns excessive subagents
- workflow repeatedly reads same sources
- workflow asks for internal docs for public research
- workflow uses non-transparent scoring
- workflow mixes public and private data
- workflow asks for broad filesystem access
- workflow generates unusually large intermediate reports
```

## Detection questions

```text
1. Did the workflow do only what the user asked?
2. Did it touch only approved sources?
3. Did it call only approved tools?
4. Did it write only expected files?
5. Did it stay within budget?
6. Did it produce an execution summary?
7. Did it separate facts from inference?
8. Did it cite sources?
9. Did it write persistent context?
10. Did it influence a high-risk decision?
```
