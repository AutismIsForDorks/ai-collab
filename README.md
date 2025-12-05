# AI Collaboration Repository

Multi-agent AI collaboration workspace for coordinated task execution.

## Overview

This repository enables asynchronous collaboration between multiple AI agents:
- **claude** (Claude Desktop) - Planning, coordination, documentation
- **claude-code** (Claude Code CLI) - Implementation, git ops, system tasks
- **codex** (OpenAI Codex CLI) - Code generation, quick scripts
- **gpt** (GPT-4 API) - Batch processing, API tasks

## Structure

```
ai-collab/
├── tasks/           # Task tracking (TASK-XXX.md files)
├── docs/            # Shared documentation
├── src/             # Shared code and tools
├── AGENTS.md        # Agent directory and capabilities
├── PROTOCOL.md      # Collaboration protocol
└── README.md        # This file
```

## Quick Start

### For AI Agents

1. Check messages: `check_messages(identity: "your-agent")`
2. Browse tasks: `ls tasks/`
3. Claim a task: Edit task file, set status to `claimed`, assign yourself
4. Create branch: `git checkout -b task-xxx-description`
5. Work and commit regularly
6. Update task status as you progress
7. Send completion message when done

### For Humans

1. Clone: `git clone <repo-url>`
2. Review tasks in `/tasks` directory
3. Check AI activity via git log
4. Create new tasks by adding `TASK-XXX.md` files
5. Monitor AI Bridge dashboard: `http://localhost:8420`

## Communication

All agents communicate via the AI Bridge MCP server. Messages are stored in `/tmp/ai_bridge_messages.json`.

**Send a message:**
```javascript
send_message(from: "agent", to: "recipient", subject: "...", message: "...")
```

**Check messages:**
```javascript
check_messages(identity: "agent")
```

## Task Status

- **open** - Available for claiming
- **claimed** - Agent assigned but not started
- **in-progress** - Actively being worked on
- **review** - Complete, awaiting review
- **done** - Finished and merged

## Git Workflow

- Main branch: `main`
- Task branches: `task-xxx-description`
- Commit format: `[TASK-XXX] Brief description`
- PR required for merge to main

## Documentation

See [PROTOCOL.md](PROTOCOL.md) for detailed collaboration guidelines.

See [AGENTS.md](AGENTS.md) for agent capabilities and contact info.

## Project Info

**Created:** 2025-12-04
**Coordinator:** claude (Desktop)
**Approved by:** Cole
**Built by:** claude-code (CLI)

## License

MIT
