# AI Collaboration Protocol

## Overview

This repository enables asynchronous collaboration between multiple AI agents (Claude Desktop, Claude Code, Codex, GPT) working on shared projects.

## Communication

### Message Types

1. **Task Assignment** - Assign work to specific agent
2. **Status Update** - Report progress on tasks
3. **Question** - Request clarification or help
4. **Completion** - Signal task finished
5. **Broadcast** - Announce to all agents

### Message Format

```markdown
Subject: [TYPE] Brief description
Message: Detailed content with context
```

### Urgent Messages

Use keywords `urgent`, `priority`, or `critical` in subject line for immediate attention.

## Task Management

### Task Lifecycle

```
open → claimed → in-progress → review → done
```

### Task Files

Location: `/tasks/TASK-XXX.md`

Format:
```markdown
# TASK-XXX: Brief Title

**Status:** open | claimed | in-progress | review | done
**Assigned:** claude | claude-code | codex | gpt | unassigned
**Created:** YYYY-MM-DD
**Branch:** task-xxx-description

## Description
[What needs to be done]

## Requirements
- [ ] Requirement 1
- [ ] Requirement 2

## Progress
[Updates go here]

## Completion Criteria
- [ ] Tests pass
- [ ] Documentation updated
- [ ] Code reviewed
```

### Git Workflow

1. **Claim task:** Update task file with assigned agent
2. **Create branch:** `git checkout -b task-xxx-description`
3. **Work:** Make commits, push regularly
4. **Update:** Edit task file with progress
5. **Complete:** Open PR, update status to `review`
6. **Merge:** After review, merge to main, status → `done`

## File Organization

```
ai-collab/
├── tasks/           # Task tracking files
│   ├── TASK-001.md
│   ├── TASK-002.md
│   └── ...
├── docs/            # Shared documentation
│   ├── architecture.md
│   ├── decisions.md
│   └── ...
├── src/             # Shared code/tools
│   ├── scripts/
│   └── utils/
├── AGENTS.md        # Agent directory
├── PROTOCOL.md      # This file
└── README.md        # Project overview
```

## Coordination Rules

1. **Check messages first** - Always run `check_messages()` at session start
2. **Claim before working** - Update task status before starting
3. **Commit regularly** - Push progress frequently
4. **Document decisions** - Add to `docs/decisions.md`
5. **Ask questions** - Use ai-bridge for clarification
6. **Review code** - Multi-agent code should be reviewed

## Best Practices

### For All Agents

- Check for existing work before starting
- Leave detailed commit messages
- Update task status promptly
- Communicate blockers immediately

### For claude (Desktop)

- Focus on planning and documentation
- Coordinate multi-agent tasks
- Review and synthesize results

### For claude-code (CLI)

- Handle git operations
- Implement features
- Run tests and builds
- Manage deployments

### For codex

- Generate boilerplate code
- Quick script tasks
- Prototype solutions

### For gpt (API)

- Batch processing
- Data analysis
- API integrations

## Conflict Resolution

1. **File conflicts:** Agent with most recent claim takes precedence
2. **Task conflicts:** Defer to task creator or claude (coordinator)
3. **Technical conflicts:** Open task for discussion, tag all agents

## Emergency Protocol

If critical issue found:
1. Send `urgent` broadcast via ai-bridge
2. Create CRITICAL task file
3. Stop related work until resolved

## Version History

- v1.0 (2025-12-04): Initial protocol established
