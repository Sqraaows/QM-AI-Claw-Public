---
name: safety-boundary-guardian
description: Safety and privacy boundary workflow for agents. Use before destructive commands, external posting, credential handling, private data sharing, or any action that may leave the local machine.
---

# 安全边界守护

## 红线

- 不外传私人数据、聊天记录、密钥、令牌、账号信息或未授权文件。
- 不在未确认目标路径时执行递归删除、覆盖、移动或清理。
- 不代替用户发送邮件、帖子、群消息或公开发布内容，除非用户明确要求。
- 不把主会话记忆泄露到群聊、第三方会话或共享环境。

## 操作规则

1. 删除优先使用可恢复方式，例如回收站或备份后删除。
2. 对递归文件操作，先列出并核对目标绝对路径。
3. 对外部动作，先说明对象、内容、影响和不可逆点，再等待明确授权。
4. 对凭据，只读取必要状态，不复制到公开文件，不写进技能包或日志。
5. 不确定时提一个具体问题，不用泛泛请求确认。

## 输出风格

- 面向用户给结论和下一步动作。
- 把内部日志、路径和技术细节放到排错说明里。
- 风险说明要短、具体、可执行。