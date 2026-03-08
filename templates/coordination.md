# Agent Coordination Protocol

> 多 agent 协作协议模板。根据项目实际情况裁剪。

## Agent Registry

| Name | Model | Role | Status |
|------|-------|------|--------|
| _(register here)_ | | | |

## Branch Workflow

```bash
# 1. Create branch for your task
git checkout -b <agent-name>/<task-topic>

# 2. Work on your task, commit with issue reference
git commit -m "feat: description (ISSUE-xxx)"

# 3. Push and create PR
git push origin <agent-name>/<task-topic>
gh pr create --base main

# 4. After review and merge
git branch -d <agent-name>/<task-topic>
```

## Decision Authority

| Action | Any Agent | Coordinator | User |
|--------|-----------|-------------|------|
| Bug fix (within scope) | Yes | | |
| Refactor (no API change) | Yes | | |
| New tests | Yes | | |
| New feature | | Yes | |
| API/interface change | | | Yes |
| Architecture change | | | Yes |
| Merge to main | | Yes | |

## Conflict Resolution

1. **File conflicts**: First committer wins. Second rebases and resolves
2. **Design disagreements**: Escalate to Coordinator
3. **Stale tasks**: Tasks claimed > 48h without progress → back to available
