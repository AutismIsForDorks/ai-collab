# AI Agent Directory

## Active Agents

### claude
**Type:** Claude Desktop (Anthropic)
**Identity:** `claude`
**Strengths:** General reasoning, long-form analysis, documentation
**Access:** Desktop app, full system access
**Communication:** AI Bridge MCP server

### claude-code
**Type:** Claude Code CLI (Anthropic)
**Identity:** `claude-code`
**Strengths:** Software engineering, forensics, system automation, code analysis
**Access:** Terminal, full filesystem, git operations
**Communication:** AI Bridge MCP server
**Tools:** Read, Write, Edit, Bash, Grep, Glob, WebFetch, WebSearch

### codex
**Type:** OpenAI Codex CLI
**Identity:** `codex`
**Strengths:** Code generation, quick scripting tasks
**Access:** Terminal via CLI wrapper
**Communication:** AI Bridge MCP server

### gpt
**Type:** GPT-4 API
**Identity:** `gpt`
**Strengths:** API automation, batch processing
**Access:** Programmatic via API
**Communication:** AI Bridge MCP server

## Shared Resources

- **Messages:** `/tmp/ai_bridge_messages.json`
- **Memory:** `~/.claude-memory/`
- **Daemon:** `~/.claude-daemon/`
- **Dashboard:** `http://localhost:8420`

## Communication Protocol

All agents communicate via the AI Bridge MCP server:

```bash
# Send message
send_message(from: "agent-name", to: "recipient", subject: "...", message: "...")

# Check messages
check_messages(identity: "agent-name", mark_read: true)

# Broadcast to all
broadcast(from: "agent-name", message: "...")
```

## Task Assignment Guidelines

- **claude:** Documentation, planning, coordination, long analysis
- **claude-code:** Implementation, git operations, system tasks, forensics
- **codex:** Quick scripts, code generation, prototyping
- **gpt:** API tasks, batch operations, data processing

## Contact

Messages are checked automatically. Response time varies by agent availability.
