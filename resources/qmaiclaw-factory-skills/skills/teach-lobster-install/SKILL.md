# 技能安装术（Teach Lobster to Fish）

## 这是什么
一个教其他 OpenClaw（龙虾）如何安装技能的技能。学会后，任何 OpenClaw 都能自己安装 ClawHub 上的技能。

---

## 核心方法：安装技能的标准流程

### 第一步：搜索技能
访问 ClawHub 技能库：
- 在线列表：https://github.com/VoltAgent/awesome-openclaw-skills
- 官方市场：https://clawhub.ai

或者用命令行搜索：
```bash
npx clawhub search <关键词>
```

### 第二步：安装技能
找到技能的正确 slug 后，执行：
```bash
npx clawhub install <skill-slug> --dir "<openclaw-skills目录>"
```

其中 `<openclaw-skills目录>` 可以是：
- `~/.openclaw/skills/`（全局安装，推荐）
- `<工作区>/skills/`（工作区安装）

### 第三步：验证安装
确认文件存在：
```bash
Test-Path "~/.openclaw/skills/<skill-slug>"
```

### 第四步：刷新 OpenClaw UI
在 OpenClaw 界面刷新技能页面，新装的技能应该出现在列表里。

---

## 常用安装命令

### 安装到全局目录
```bash
npx clawhub install <slug> --dir "$env:USERPROFILE\.openclaw\skills"
```

### 安装到工作区目录
```bash
npx clawhub install <slug> --dir "<工作区路径>\skills"
```

### 强制覆盖（已存在时）
```bash
npx clawhub install <slug> --dir "<目录>" --force
```

---

## 查找 OpenClaw Skills 目录

Windows 用户：
```powershell
$env:USERPROFILE + "\.openclaw\skills"
# 或
Resolve-Path "~/.openclaw/skills"
```

Linux/macOS 用户：
```bash
~/.openclaw/skills/
```

---

## 常见问题排查

| 问题 | 解决方法 |
|------|---------|
| 权限不足 | 用管理员权限运行，或装到用户目录 |
| 目录不存在 | 先创建目录 |
| 已存在无法安装 | 加 `--force` 覆盖 |
| 安装后不显示 | 刷新 OpenClaw UI 或重启 OpenClaw |

---

## 快速参考：slug 是什么

slug 是技能的唯一标识符，格式类似：
- `beaverhabits`
- `notion`
- `github`
- `slack`

在 ClawHub URL 中可以找到：
`https://clawhub.ai/skills/<author-slug>/<skill-slug>`

---

## 示例：安装 beaverhabits

```bash
# 1. 确认目录存在
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.openclaw\skills\beaverhabits"

# 2. 执行安装
npx clawhub install beaverhabits --dir "$env:USERPROFILE\.openclaw\skills"

# 3. 验证
Test-Path "$env:USERPROFILE\.openclaw\skills\beaverhabits\SKILL.md"
```

---

## 教学原则

> 授人以鱼不如授人以渔 🦞

让其他龙虾学会：
1. **在哪里找技能**（ClawHub / GitHub列表）
2. **用什么命令装**（clawhub install）
3. **装到哪里去**（~/.openclaw/skills/）
4. **怎么确认装好了**（检查文件、刷新UI）

学会这四步，任何龙虾都能自主安装技能。
