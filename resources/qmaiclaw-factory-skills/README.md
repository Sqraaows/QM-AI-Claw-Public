# 曲美智家超级小龙虾增值技能库

这是给 OpenClaw / QM Claw 使用的独立增值技能仓库，从 `增值技能.zip` 中整理出可复用、可发布的轻量技能包。

仓库入口：

- `aion-extension.json`：AionUi/OpenClaw 扩展清单
- `skills/`：技能目录，每个技能都有自己的 `SKILL.md`

## 已包含技能

- `train-12306`：12306 查票与站点查询
- `siliconflow-all`：硅基流动多模态路由与转写脚本
- `image-process`：小龙虾修图、压缩、格式转换、背景处理
- `aicharmer`：MiniMax / SiliconFlow 图片和视频生成
- `ecommerce-listing`：电商商品上下架计划、CSV 和抖音请求预演
- `digital-human-voiceover`：数字人口播脚本
- `old-photo-restoration`：老照片修复
- `old-photo-animation`：老照片动起来
- `video-editor`：本地视频基础剪辑
- `ai-manga-drama`：AI 漫剧分镜、视频任务和字幕流程
- `siliconflow-video-gen`：硅基流动文生/图生视频任务
- `siliconflow-keyframe-video-outfit`：关键帧换装视频

## 安全处理

本仓库只保留适合发布的轻量内容，已排除：

- API key、真实账号 token、本地私有配置
- `node_modules`、package lock、日志、生成导出文件
- FFmpeg、whisper、模型权重、大型二进制文件
- 大体积样例媒体、历史项目输出
- 机器和用户绑定的“超级小龙虾大脑”工作区状态

云端技能默认读取环境变量，例如：

- `SILICONFLOW_API_KEY`
- `MINIMAX_API_KEY`
- `LIUDONG_ACCESS_TOKEN`
- `VOLCENGINE_ACCESS_KEY_ID`
- `VOLCENGINE_SECRET_ACCESS_KEY`

不要把真实 key 写进仓库。

## OpenClaw 使用

如果 OpenClaw 支持从扩展仓库安装，使用本仓库根目录即可；如果是手动安装，把需要的子目录复制到 OpenClaw 的 skills 目录：

```text
skills/<技能名>/SKILL.md
```

视频剪辑、修图等技能可能需要本机安装 Node、Python、FFmpeg 或按技能目录里的说明下载可选依赖。依赖和模型只放本机，不提交回仓库。
