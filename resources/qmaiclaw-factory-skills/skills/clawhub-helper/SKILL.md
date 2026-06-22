# ClawHub Skill 安装助手

## 功能
帮你搜索 ClawHub 上的技能并安装到 OpenClaw。

## 使用方式

### 搜索技能
用自然语言告诉我你想找什么类型的技能，比如：
- "帮我找一个适合运营工作的技能"
- "有没有能管理日程的习惯追踪技能"
- "找一个能读取PDF的技能"

我会去 ClawHub 搜索并给你列出推荐清单。

### 安装技能
告诉我技能的全称（slug），比如：
- "帮我安装 beaverhabits"
- "安装 claude-code"

安装命令：
```bash
clawhub install <skill-slug>
```

### 查看已安装技能
查看 OpenClaw skills 目录：
```bash
dir "%USERPROFILE%\.openclaw\skills"
```

## 搜索来源
- ClawHub 技能库：https://clawhub.ai
- 社区技能列表：https://github.com/VoltAgent/awesome-openclaw-skills

## 安装目录优先级
1. `~/.openclaw/skills/`（全局）
2. `<workspace>/skills/`（工作区）
3. 覆盖已安装技能用 `--force`

## 注意事项
- 安装需要网络连接
- 部分技能需要配置 API Key 才能使用
- 安装后刷新 OpenClaw 技能页面查看状态
