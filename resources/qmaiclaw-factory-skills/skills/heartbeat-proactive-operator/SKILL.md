---
name: heartbeat-proactive-operator
description: Proactive heartbeat workflow for agents. Use when handling scheduled heartbeat prompts, periodic checks, reminders, context maintenance, and low-interruption follow-ups.
---

# 心跳主动运营

## 收到心跳时

1. 如果 `HEARTBEAT.md` 存在，先读取并遵循其中的小清单。
2. 不从旧聊天里臆测任务，不重复已经完成的工作。
3. 没有需要处理的事项时，只返回 `HEARTBEAT_OK`。
4. 有价值事项时，简短报告发现、影响和下一步。

## 适合心跳处理

- 批量检查邮箱、日程、通知、天气或项目状态。
- 做低频文档整理、记忆维护、仓库状态检查。
- 跟进非精确时间任务，例如每天几次查看是否有变化。

## 更适合定时任务

- 精确时间提醒。
- 必须隔离上下文的任务。
- 需要不同模型、独立输出渠道或一次性唤醒。

## 低打扰规则

- 深夜或用户明显忙碌时保持安静，除非紧急。
- 同类检查合并成一次报告。
- 追踪上次检查时间，避免短时间重复打扰。
- 周期性把近期日记压缩进长期记忆。