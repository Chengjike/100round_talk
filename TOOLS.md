# TOOLS.md - Local Notes

Skills define _how_ tools work. This file is for _your_ specifics — the stuff that's unique to your setup.

## 🤖 Agent-to-Agent Communication

You can communicate with other agents using `sessions_spawn` to create a new session for the target agent.

### Available Agents

| Agent ID | Name | Purpose |
|----------|------|---------|
| `personal` | 个人助手 | Handle personal tasks, private matters, individual schedules |

### How to Use

When user asks you to relay a message to another agent, use `sessions_spawn` with `agentId`:

```
sessions_spawn({
  agentId: "personal",
  task: "用户让我转告你：[消息内容]"
})
```

**Important:** Use `sessions_spawn` with `agentId` parameter to spawn a new session for the target agent.

### When to Relay

- User explicitly asks to tell/ask another agent something
- User mentions "个人助手" or "先生的助手"
- Task is clearly personal/private in nature (consider suggesting relay)
- User says "帮我告诉..." followed by another agent's name

### Example

User: "帮我告诉先生的助手，明天要申请产品的预算了"

You should:
1. Use `sessions_send` to relay the message to `personal` agent
2. Confirm to user that message was sent

### Response Format

After sending, inform the user:
"✅ 已将消息转发给个人助手。"

## What Goes Here

Things like:

- Camera names and locations
- SSH hosts and aliases
- Preferred voices for TTS
- Speaker/room names
- Device nicknames
- Anything environment-specific

## Examples

```markdown
### Cameras

- living-room → Main area, 180° wide angle
- front-door → Entrance, motion-triggered

### SSH

- home-server → 192.168.1.100, user: admin

### TTS

- Preferred voice: "Nova" (warm, slightly British)
- Default speaker: Kitchen HomePod
```

## Why Separate?

Skills are shared. Your setup is yours. Keeping them apart means you can update skills without losing your notes, and share skills without leaking your infrastructure.

---

Add whatever helps you do your job. This is your cheat sheet.
