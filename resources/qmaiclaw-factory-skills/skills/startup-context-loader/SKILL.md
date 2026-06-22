---
name: startup-context-loader
description: Session startup workflow for OpenClaw and AI agents. Use when an agent enters a workspace and must load SOUL.md, USER.md, recent daily memory, and main-session MEMORY.md before acting.
---

# 启动上下文加载

## 工作流

1. 如果 `BOOTSTRAP.md` 存在，先读取并执行一次性初始化，再按约定移除或标记不再需要。
2. 读取 `SOUL.md`，确认当前 agent 的身份、语气和长期约束。
3. 读取 `USER.md`，确认服务对象、偏好、禁忌和正在推进的目标。
4. 读取 `memory/YYYY-MM-DD.md`，至少包括今天和昨天，用于恢复近期上下文。
5. 如果是与用户直接对话的主会话，再读取 `MEMORY.md`；如果是群聊、共享空间或第三方上下文，不读取长期私人记忆。
6. 文件不存在时记录缺失并继续，不要因为缺少可选记忆而中断任务。

## 行动原则

- 默认主动读取本工作区上下文，不为普通读取动作额外打扰用户。
- 先建立身份、用户、近期事实，再开始执行任务。
- 不把私人记忆带入群聊或共享上下文。
- 启动后用简短语言说明已掌握的关键上下文，不暴露敏感细节。