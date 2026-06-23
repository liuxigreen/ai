# 女娲 · AI短剧工厂 Skill 套装

9 个专家级 Skill，按女娲蒸馏法打造，覆盖从热点发现到发布运营的完整 AI 短剧创作流水线。

## 安装

将所有文件夹放入 `~/.workbuddy/skills/`（全局）或 `.workbuddy/skills/`（项目级）。

## Skill 清单

| # | Skill | 功能 | 蒸馏了什么 |
|---|-------|------|-----------|
| 1 | `hotspot-discovery` | 热点发现 | 多平台热榜、情绪拆解、四维框架 |
| 2 | `short-drama-screenwriting` | 短剧编剧 | 杨玉鲁/黄经天/洛古特/贾毅/王晨 + 麦基/救猫咪 |
| 3 | `ai-cinematography` | 画面指令 | 王家卫/韦斯/刘梓瑜 + awesome-gpt-image-2 |
| 4 | `ai-image-generation` | 生图执行 | 字节工具链 + ComfyUI + 分镜方法论 |
| 5 | `ai-video-generation` | 生视频 | 可灵/即梦/Runway + 镜头运动语法 |
| 6 | `ai-video-editing` | 剪辑节奏 | 短视频节奏 + 蒙太奇理论 + AI后期 |
| 7 | `ai-sound-design` | 声音设计 | 抖音BGM + 剪映音效库 + AI配音 |
| 8 | `ai-publishing` | 发布运营 | 标题/封面/标签/时间/数据/分发 |
| 9 | `nuwa-pipeline` | 一键总控 | 调度8站自动接力，pipeline.json共享数据 |

## 使用方式

**一键启动：**

> 帮我做一部职场逆袭短剧

Agent 自动走 8 站：热点 → 编剧 → 画面 → 生图 → 生视频 → 剪辑 → 声音 → 发布。

**单站调用：**

> 帮我写一个甜宠短剧剧本
> 把这个剧本转成分镜Prompt
> 推荐这个片段的BGM和音效

## Dashboard

打开 `projects/nuwa-dashboard.html` 查看交互式流水线可视化界面。

## 依赖

- 所有 Skill 输出基于公开工具（剪映/即梦/可灵/ComfyUI等），不依赖特定API
- 实际生图/生视频需用户在对应工具中手动执行

## 许可

MIT
