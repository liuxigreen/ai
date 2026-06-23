# 女娲 · AI短剧工厂 Skill 套装

9 个专家级 Skill，按女娲蒸馏法打造，覆盖从热点发现到发布运营的完整 AI 短剧创作流水线。200+ 独立来源蒸馏。

---

## 一键安装

**在 WorkBuddy 对话中直接输入：**

```
安装 skill https://github.com/liuxigreen/ai
```

或点击：[一键安装到 WorkBuddy](https://www.codebuddy.cn/docs/workbuddy/Overview)

---

## 手动安装

```bash
# 克隆到全局 Skills 目录
git clone git@github.com:liuxigreen/ai.git ~/.workbuddy/skills/nuwa-skills

# 或者克隆到项目级
git clone git@github.com:liuxigreen/ai.git .workbuddy/skills/nuwa-skills
```

安装后重启 WorkBuddy 或刷新 Skills 列表即可。

---

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

---

## 使用方式

### 一键启动（推荐）

> 帮我做一部职场逆袭短剧

Agent 自动走 8 站：热点 → 编剧 → 画面 → 生图 → 生视频 → 剪辑 → 声音 → 发布。

### 单站调用

> 帮我写一个甜宠短剧剧本
>
> 把这个剧本转成分镜 Prompt
>
> 推荐这个片段的 BGM 和音效
>
> 给成片出一个封面标题方案

---

## 端到端示例

输入：**「加班改17版方案被关系户冒名」**

| 阶段 | 产出 |
|------|------|
| 🔍 热点发现 | 情绪拆解：愤怒→逆袭，框架：被低估者→离开→证明更值钱 |
| ✍️ 编剧 | 5镜×15镜剧本，王家卫情绪都市风格 |
| 🎬 画面指令 | 5条结构化 Prompt + 200词角色卡片(林雪) |
| 🖼️ 生图 | 即梦 S2.0 参数：Seed123456 / 3S抽卡 / 定妆照 |
| 🎥 生视频 | 可灵 3.0 运镜序列 + 首尾帧链 |
| ✂️ 剪辑 | 3-5-15-40 节奏网格 + 光闪卡点 |
| 🎵 声音 | BGM：低沉钢琴→温暖弦乐，三明治音轨 |
| 🚀 发布 | 3版标题 A/B 测试 + 18:00 首发 |

---

## 依赖

- 所有 Skill 输出基于公开工具（剪映/即梦/可灵/ComfyUI 等），不依赖特定 API
- 实际生图/生视频需用户在对应工具中手动执行

---

## 许可

MIT
