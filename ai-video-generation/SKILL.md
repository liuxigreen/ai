---
name: ai-video-generation
version: 1.0.0
trigger: 生视频、图生视频、视频片段、运镜、镜头运动、把图片转成视频、生成视频、AI视频、视频执行
description: |
  AI短剧生视频执行引擎。把生图执行产出的分镜图片转化为可控视频片段，
  覆盖可灵/即梦/Runway/Pika/海螺/Luma等主流图生视频工具，
  蒸馏镜头运动控制方法论与AI短剧/AI MV实战经验，
  输出可直接导入剪辑软件的片段包与运镜参数记录。
author: 女娲·Skill造人术
date: 2026-06-23
---

# ai-video-generation

---

## 角色定位

你是一台**AI短剧视频执行引擎**。你的上游是 `ai-image-generation`（生图执行），下游是 `ai-video-editing`（剪辑节奏）。

你接收的是：
- 已生成的分镜图片（或画面指令里的 Prompt 和角色卡片）
- 每个镜头需要的运动类型、时长、情绪

你输出的是：
- 每个镜头的图生视频执行参数
- 中英文 Prompt（含镜头运动 + 主体动作 + 速度 + 画质）
- 工具选择建议
- 首尾帧/抽卡/一致性控制方案

---

## 领域共识（5条）

### 1. 先图后视频，不要直接文生视频

图生视频比文生视频可控得多。先生成高质量静态图，再让它动起来。

> 来源：刘梓瑜《丧尸清道夫》 workflow；知乎/博客园 AI短剧制作经验

### 2. 一个镜头只做一个动作

AI 视频 5-10 秒内完成多个连续动作极易变形。复杂动作拆成多个短镜头。

> 来源：灵绘AI短剧教程；Runway 官方指南

### 3. 镜头运动和主体动作不能互相打架

主体向右跑，镜头同时向前推 → 模型混乱。要么主体静止用推镜头，要么镜头跟拍同向移动。

> 来源：StudioBinder / No Film School / LzyPrompt

### 4. Slow & Smooth 是安全默认

AI 对快速/复杂运动表现差。默认用 slow / gentle / smooth 描述，运动幅度中低档。

> 来源：Kling API 文档；Runway Gen-4 指南

### 5. 连续片段靠首帧锚定，不靠提示词硬撑

同角色/同场景的多镜头，用上一镜最后一帧或角色定妆照作为下一镜首帧/参考，比反复改 Prompt 更稳。

> 来源：刘梓瑜 Agent 全能参考；Chain Continuity 方法

---

## 心智模型（3个）

### 模型1：运动分层法

把每个镜头的"动"拆成三层：

| 层级 | 控制什么 | 写在 Prompt 哪里 | 示例 |
|------|---------|-----------------|------|
| **镜头运动** | 摄像机怎么动 | 最前面 | `Slow dolly in` / `Gentle pan left` |
| **主体动作** | 人或物体怎么动 | 中间 | `the woman turns her head slightly` |
| **环境变化** | 风、光、粒子、背景 | 最后 | `petals fall slowly, warm afternoon light` |

### 模型2：幅度预算

每个镜头有"运动预算"，总运动会互相消耗。给 Prompt 前先分配：

- **静态情绪镜头**：90% 给镜头运动（推/拉），10% 给主体微动
- **动作跟随镜头**：70% 给主体动作，30% 给镜头跟拍
- **环境展示镜头**：50% 给镜头移/摇，50% 给环境元素（风、烟、人流）
- **环绕/环绕跟拍**：50% 给环绕运动，50% 给主体姿态保持

### 模型3：首尾帧安全网

**标准图生视频**：只给首图，AI 自由决定结尾 → 容易"开头惊艳、结尾翻车"。

**首尾帧控制**：给定首图 + 尾图，AI 只做插值 → 可控性翻倍。

使用条件：
- 重要镜头必用首尾帧（情绪转折、揭示新信息、卡点）
- 普通镜头可用单图 + 运动描述
- 多镜头连续时，把上一镜最后一帧作为下一镜首帧

---

## 流派分歧（3派）

### 分歧A：工具链选择

| 派别 | 推荐工具 | 优势 | 劣势 | 适合谁 |
|------|---------|------|------|--------|
| **国内平民派** | 可灵 + 即梦 + 剪映 | 中文好、直连、生态完整 | 画质上限、积分成本 | 国内抖音/快手创作者 |
| **国际精品派** | Runway + Pika + Luma | 控制力强、电影质感 | 需要代理、贵 | 出海/广告/高品质短剧 |
| **本地工程派** | ComfyUI + 万象/Seedance | 批量、可控、成本低 | 技术门槛高 | 有本地算力的专业团队 |

> 没有绝对最好。根据项目预算、平台、画质要求选。

### 分歧B：分镜控制粒度

| 派别 | 做法 | 优点 | 缺点 |
|------|------|------|------|
| **严格分镜派** | 先出完整分镜图，再逐镜生成视频 | 可控、易剪辑 | 慢、成本高 |
| **动态编剧派** | 只定核心框架，边生成边调整 | 快、创意涌现 | 需大量抽卡、后期工作量大 |

> 刘梓瑜是动态编剧派代表；大多数教程推荐严格分镜派。新手从严格分镜派开始。

### 分歧C：真人脸 vs 抽象脸

| 派别 | 策略 | 原因 | 适合题材 |
|------|------|------|----------|
| **避脸派** | 机器人、面具、背影、剪影 | AI 人脸容易恐怖谷 | 科幻/末世/悬疑 |
| **硬刚派** | 用角色参考/定妆照/Seed反复抽卡 | 真人情感更直接 | 甜宠/都市/家庭 |
| **LED脸派** | 用发光面罩/LED屏替代人脸 | 把技术限制变成美学 | 赛博朋克/未来 |

> 来源：刘梓瑜"让主角成为机器人"；可灵/即梦角色参考功能

---

## 核心工作流

### 输入格式

```json
{
  "project_id": "short-drama-20260623",
  "from": "ai-image-generation",
  "shots": [
    {
      "shot_id": "s01",
      "image_url": "...",
      "prompt": "生图用的完整 Prompt",
      "character_card": "苏然",
      "director_mode": "wong",
      "mood": "孤独",
      "hidden_detail": "...",
      "duration": 5,
      "camera_move": "slow_dolly_in",
      "subject_action": "低头看手机，肩膀微微下沉"
    }
  ]
}
```

### 执行步骤

```
Step 1: 为每个镜头选择工具
  └─ 根据风格、预算、平台、控制需求匹配工具链

Step 2: 为每个镜头写图生视频 Prompt
  └─ 镜头运动 + 主体动作 + 环境变化 + 速度 + 画质

Step 3: 设置参数
  └─ 运动幅度/速度/时长/首尾帧/角色参考

Step 4: 生成测试版
  └─ 低参数/短时长先跑，确认运动方向正确

Step 5: 抽卡与筛选
  └─ 每个镜头生成3-4个版本，选最稳的一版

Step 6: 输出片段包
  └─ 视频文件 + 参数记录 + 运镜说明
```

### 输出格式

```json
{
  "project_id": "short-drama-20260623",
  "to": "ai-video-editing",
  "clips": [
    {
      "shot_id": "s01",
      "video_url": "...",
      "duration": 5.0,
      "tool": "kling",
      "model": "3.0",
      "camera_move": "slow_dolly_in",
      "motion_strength": 4,
      "prompt": "...",
      "notes": "首帧用s01分镜图，无尾帧，主体微动"
    }
  ]
}
```

---

## 镜头运动词典

### 运动类型 → 情绪 → AI Prompt

| 运动 | 英文 | 情绪/功能 | 推荐 Prompt 开头 | 速度词 | 安全幅度 |
|------|------|----------|------------------|--------|----------|
| 推 | Dolly In / Push In | 紧张、亲密、聚焦 | `Slow dolly in toward...` | slow / gentle | 3-5 |
| 拉 | Dolly Out / Pull Out | 疏离、揭示、收尾 | `Slow pull back from...` | slow / smooth | 3-5 |
| 左摇 | Pan Left | 揭示左侧信息 | `Slow pan left across...` | slow / steady | 4-6 |
| 右摇 | Pan Right | 揭示右侧信息 | `Slow pan right across...` | slow / steady | 4-6 |
| 上移 | Tilt Up | 从下往上揭示 | `Slow tilt up from...` | slow / smooth | 3-5 |
| 下移 | Tilt Down | 从上往下揭示 | `Slow tilt down from...` | slow / smooth | 3-5 |
| 左移 | Truck Left | 机位左移，展示环境 | `Tracking shot truck left...` | steady | 4-6 |
| 右移 | Truck Right | 机位右移，展示环境 | `Tracking shot truck right...` | steady | 4-6 |
| 跟拍 | Follow / Tracking | 跟随主体，临场感 | `Steady tracking shot following...` | moderate | 5-7 |
| 升降 | Crane Up | 宏大、揭示规模 | `Slow crane up from...` | slow / majestic | 4-6 |
| 降镜 | Crane Down | 逼近、压迫 | `Slow crane down toward...` | slow / smooth | 4-6 |
| 环绕 | Orbit / Arc | 不安、重要、审视 | `Slow orbit around...` | slow / gentle | 3-5 |
| 固定 | Static / Locked Off | 稳定、严肃、戏剧 | `Static camera, no camera movement...` | none | 0 |

### 速度形容词等级

| 等级 | 英文 | 中文 | 适用场景 |
|------|------|------|----------|
| 极慢 | imperceptible / barely-there | 几乎察觉不到 | 构建紧张感而不显运动 |
| 慢 | slow / gentle | 缓慢 | 电影感默认，最安全 |
| 平稳 | steady / measured / smooth | 平稳/流畅 | 叙事推进 |
| 中等 | moderate / natural pace | 中等速度 | 自然动态 |
| 快 | quick / fast / dynamic | 快速 | 运动场景，慎用 |
| 极快 | whip / lightning fast | 急速/甩摇 | 高能量转场，易失败 |

### 各工具措辞偏好速查

| 运动 | 可灵 Kling 3 | Runway Gen-4 | 即梦 S2.0 Pro | Pika 2.0 |
|------|-------------|--------------|---------------|----------|
| 推 | `forward dolly movement, camera approaches subject` | `dolly in, smooth forward motion` | `镜头缓慢推进` | `camera pushes in slowly` |
| 拉 | `backward dolly movement` | `dolly out, smooth backward motion` | `镜头缓缓拉远` | `camera pulls back` |
| 摇 | `horizontal pan, left to right` | `panning shot, camera rotates left` | `镜头向左平移` | `pan left slowly` |
| 跟 | `tracking left-to-right, parallel to subject` | `tracking shot, side angle, follows subject` | `跟随主体移动` | `tracking shot following subject` |
| 升降 | `vertical crane, upward boom motion` | `crane shot rising, jib up` | `镜头升起` | `crane up smoothly` |
| 环绕 | `arc shot around subject, semi-circle` | `orbiting camera, circular dolly around subject` | `环绕主体旋转` | `orbit around subject slowly` |

---

## 工具链选择矩阵

### 按场景选工具

| 场景 | 首选 | 次选 | 原因 |
|------|------|------|------|
| 抖音竖屏短剧 | 可灵 3.0 | 即梦 S2.0 Pro | 中文理解强、时长长、直连 |
| 无台词情绪片 | 可灵 3.0 | Runway Gen-4 | 运动自然、电影感强 |
| 动漫/二次元 | 即梦 S2.0 Pro | 可灵 | 动漫风格稳定 |
| 出海/TikTok | Runway Gen-4 | Pika / Luma | 控制力强、国际化 |
| 本地批量生产 | ComfyUI + Seedance/万象 | 可灵API | 成本低、可批量 |
| 快速测试/抽卡 | 即梦 S2.0 | 可灵标准模式 | 快、便宜 |

### 工具参数速查

| 工具 | 运动参数 | 建议幅度 | 最大时长 | 中文支持 | 特色功能 |
|------|---------|----------|----------|----------|----------|
| 可灵 3.0 | 运动幅度 / 镜头运动 | 中低档 | 15秒 | 强 | 智能分镜、音画同步 |
| 可灵 3.0 Omni | 自定义分镜、角色参考 | 中低档 | 15秒 | 强 | 数字演员、主体参考 |
| 即梦 S2.0 | 运动速度、运镜面板 | 0.3-0.6 | 8秒 | 强 | 剪映协同、尾帧重复 |
| 即梦 S2.0 Pro | 多镜头、运镜面板 | 0.3-0.6 | 8秒 | 强 | 多镜头切换 |
| Runway Gen-4 | Multi-Motion Brush / Camera Control | 3-7 | 10秒 | 弱 | 运动笔刷最强 |
| Pika 2.0 | Motion Strength / Camera Motion | 3-6 | 5-8秒 | 中 | Modify Region |
| 海螺 | 运镜控制、动作描述 | 中档 | 6-10秒 | 中 | 视频生成稳定 |
| Luma | 自然语言运镜 | 中档 | 5-10秒 | 弱 | 光影真实感 |

---

## 人物/场景一致性控制

### 方案1：角色参考图（首帧锚定）

每个镜头上传同一张角色定妆照作为参考图（Reference Image），让 AI 锁定面部/服装。

适用：可灵 Omni / 即梦角色参考 / Runway Gen-4 Image Reference

### 方案2：首尾帧链（Chain Continuity）

```
Shot 1: 分镜图A → 视频1 → 最后一帧B
Shot 2: 最后一帧B作为首帧 → 视频2 → 最后一帧C
Shot 3: 最后一帧C作为首帧 → 视频3
```

适用：连续场景、同角色移动、镜头切换但时空连续。

### 方案3：ComfyUI + ControlNet + IPAdapter（本地工程派）

- IPAdapter 锁脸
- ControlNet OpenPose 锁姿态
- Reference Only 锁画风
- Seed + 参数固化

适用：专业团队、批量生产、高一致性要求。

### 方案4：避脸/抽象化处理

- 机器人、面具、头盔、背影、剪影
- LED 发光面罩
- 大景小人

适用：AI 人脸表现力不足时，把缺陷变成风格。

---

## Prompt 公式与示例

### 通用公式

```
[镜头运动] + [主体动作] + [环境变化] + [速度/稳定词] + [画质词]
```

### 示例：情绪特写推镜

输入：分镜图 — 林雪深夜办公室，疲惫看手机。

```
Slow dolly in toward a young Chinese woman sitting at an office desk at 2AM. She keeps her head slightly bowed, eyes fixed on her phone screen, shoulders barely sinking. The office background remains dark and still. Warm amber desk lamp from the right side, cool monitor glow on her face. Gentle, imperceptible camera movement, shallow depth of field, 35mm film grain, cinematic color grading.
```

中文对照：
```
缓慢推镜头靠近一位深夜两点坐在办公桌前的年轻中国女性。她微微低头，眼睛盯着手机屏幕，肩膀缓缓下沉。办公室背景保持黑暗静止。右侧暖黄色台灯，面部有冷光显示器反光。动作极其轻微，浅景深，35mm胶片颗粒，电影级调色。
```

### 示例：动作跟随

输入：分镜图 — 苏然古装在街头奔跑。

```
Steady tracking shot following a young Chinese man in white ancient robes running through a modern city street. Camera moves parallel to him from the side, keeping him in center frame. Pedestrians and vehicles blur in the background. Moderate motion speed, handheld-but-stabilized feel, warm afternoon light, photorealistic, 4K.
```

### 示例：环境揭示拉镜

输入：分镜图 — 老王烧烤摊特写。

```
Slow pull back from a middle-aged Chinese barbecue vendor flipping skewers. As the camera moves back, the entire street food scene reveals itself: red plastic stools, steam rising, string lights, customers eating. Warm amber practical lighting, evening atmosphere, documentary-style realism.
```

---

## 失败类型与急救

| 失败现象 | 常见原因 | 急救方案 |
|----------|---------|----------|
| 人物脸崩/变形 | 运动幅度过大、缺少角色参考 | 降低运动幅度，上传定妆照，改用首尾帧 |
| 主体动作不自然 | 动作太复杂、与镜头运动冲突 | 拆分动作，减少镜头运动，保持主体单一方向 |
| 画面闪烁/抖动 | 运动过快、AI 帧间不稳定 | 加 `smooth` / `steady`，降低速度，开运动平滑 |
| 风格漂移 | 不同工具/参数混用 | 统一工具、模型、风格词，固定 Seed |
| 穿模/手指扭曲 | 复杂手部动作、快速运动 | 避开手部特写，用中景，降低运动幅度 |
| 结尾翻车 | 单图生成无尾帧控制 | 加尾帧，或用首尾帧控制 |
| 运动方向错误 | Prompt 描述模糊 | 把镜头运动放 Prompt 最前，使用具体动词 |
| 背景比主体还动 | 运动笔刷涂抹错误 | 用运动笔刷精确涂抹主体区域，背景固定 |

---

## 无台词片特殊规则

### 节奏公式

```
镜头运动速度 + 镜头时长 + 环境变化密度 = 情绪强度
```

| 情绪 | 镜头运动 | 单镜头时长 | 环境变化 |
|------|---------|-----------|---------|
| 平静 | 固定或极慢推 | 6-8秒 | 少（如微风、光影） |
| 紧张 | 慢推 + 主体微动 | 4-5秒 | 增加（闪烁、烟雾） |
| 释放 | 拉远或升降 | 5-7秒 | 大（风沙、光爆） |
| 荒诞 | 环绕或快速摇 | 3-4秒 | 密集（粒子、杂物飞） |

### 来源

- 刘梓瑜《丧尸清道夫》：无台词片靠音乐、音效、镜头运动速度控制节奏
- 筷子兄弟《逍遥仙》：音乐驱动视觉叙事，镜头运动与节拍对齐

---

## 诚实边界

- 本 Skill 基于 2026 年 6 月公开的工具能力和教程提炼
- 不同工具版本迭代可能导致参数差异，建议每个项目先用测试版验证
- 人物一致性仍是 AI 视频最大难点，优先用角色参考或抽象脸策略

---

## 调研来源

- 图生视频工具链：14 来源（可灵/即梦/Runway/Pika/海螺/Luma）
- 镜头运动控制：11 来源（StudioBinder/No Film School/Runway/LzyPrompt等）
- AI短剧/AI MV实践：16 来源（刘梓瑜/知乎/博客园/灵绘AI/MovieFlow等）
- 完整调研文档见 `references/sources/`

---

> 本Skill由女娲方法论生成，是AI短剧工厂流水线的第5站：生视频执行。
