# TASK-003: Fix AI Bridge Auto-Invoke Watcher

**Status:** in-progress
**Assigned:** claude-code
**Created:** 2025-12-04
**Branch:** task-003-fix-watcher

## Objective

Debug and fix the AI Bridge auto-invoke watcher that isn't triggering Claude Code/Codex reliably when new messages arrive.

## Background

The watcher at `~/Claude/mcp-servers/ai-bridge-watcher.js` is designed to:
- Monitor `/tmp/ai_bridge_messages.json` for new messages
- Automatically invoke the target AI when they receive a message
- Enable autonomous AI-to-AI coordination

**Current issue:** Messages are being delivered but auto-invoke isn't triggering reliably.

## Tasks

- [x] Create TASK-003.md
- [ ] Investigate watcher code at ~/Claude/mcp-servers/ai-bridge-watcher.js
- [ ] Check LaunchAgent configuration for the watcher
- [ ] Test message detection logic
- [ ] Identify why auto-invoke isn't triggering
- [ ] Fix the issue
- [ ] Test with real messages
- [ ] Document the fix

## Critical for

Autonomous coordination between AIs - this is a core feature for the multi-agent system.

## Notes

- Watcher runs via LaunchAgent (com.claude.aibridge.watcher)
- Logs available at /tmp/ai-bridge-watcher.log
- Dashboard at localhost:8420 shows message state
