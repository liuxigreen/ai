---
name: nuwa-pipeline
version: 1.0.0
trigger: 一键短剧、做短剧、拍短剧、AI短剧工厂、帮我做一部短剧、做一个视频、创作短剧
description: |
  AI短剧工厂一键总控。输入一个创意/热点/关键词，自动按顺序调度8个专家Skill：
  热点发现→编剧→画面指令→生图执行→生视频→剪辑节奏→声音设计→发布运营。
  每个环节输出JSON到共享工作目录，下一个环节自动读取。
author: 女娲·Skill造人术
date: 2026-06-23
---

# nuwa-pipeline

---

## 操作方式

当用户说「帮我做一部[题材/创意]短剧」，按以下顺序执行：

### Stage 0：环境初始化

创建项目目录和共享数据文件：
- `C:\Users\LENOBO\WorkBuddy\2026-06-22-23-53-33\projects\{project_id}\`
- `C:\Users\LENOBO\WorkBuddy\2026-06-22-23-53-33\projects\{project_id}\pipeline.json`

初始化 pipeline.json：
```json
{
  "project_id": "",
  "created_at": "",
  "user_input": "",
  "stages": {
    "hotspot": { "status": "pending" },
    "script": { "status": "pending" },
    "cinematography": { "status": "pending" },
    "image_gen": { "status": "pending" },
    "video_gen": { "status": "pending" },
    "editing": { "status": "pending" },
    "sound": { "status": "pending" },
    "publishing": { "status": "pending" }
  }
}
```

### Stage 1：热点发现

加载 `.workbuddy/skills/hotspot-discovery/SKILL.md`

**要做的事**：
- 为用户的输入（关键词/题材/创意）搜索当前热榜
- 输出选题包：情绪拆解、冲突分析、人设提炼、框架提取、增量点
- 写入 pipeline.json → hotspot 字段

**输出示例**：
```json
"hotspot": {
  "title": "...",
  "emotion_engine": {...},
  "four_d_breakdown": {...},
  "adaptation": {...}
}
```

**完成后**：更新 pipeline.json stage status → completed。

### Stage 2：短剧编剧

加载 `.workbuddy/skills/short-drama-screenwriting/SKILL.md`

**要做的事**：
- 读取 pipeline.json 的 hotspot 数据
- 按四阶段流：题材选择→结构搭建→写作执行→生成前3集剧本
- 输出15镜短片剧本（或80集前3集试播本）
- 写入 pipeline.json → script 字段

**完成后**：更新 status。

### Stage 3：画面指令

加载 `.workbuddy/skills/ai-cinematography/SKILL.md`

**要做的事**：
- 读取 script 中的分集/分镜文本
- 为每个镜头生成7模块结构化Prompt
- 建立角色卡片（方案一200词级别）
- 选择导演模式（王/韦/末世），或按用户偏好
- 写入 pipeline.json → shots 字段

**完成后**：更新 status。

### Stage 4：生图执行

加载 `.workbuddy/skills/ai-image-generation/SKILL.md`

**要做的事**：
- 读取 shots 中的 Prompt 和角色卡片
- 按工具链路（平民/精品/工业化）选择工具和参数
- 生成每个镜头的生图执行指令（含CHAR资产、抽卡策略、Seed）
- 保存图片到 `projects/{project_id}/images/`
- 写入 pipeline.json → images 字段

**注意**：这一步需要使用 ImageGen 工具实际生成图片。如果没有对应工具或工具不可用，输出「生图准备清单」供用户在即梦/可灵中手动执行。

**完成后**：更新 status。

### Stage 5：生视频

加载 `.workbuddy/skills/ai-video-generation/SKILL.md`

**要做的事**：
- 读取 images 中的分镜图
- 为每个镜头生成图生视频 Prompt（镜头运动+主体动作+环境变化）
- 选择工具链和参数（运动幅度、速度、首尾帧等）
- 写入 pipeline.json → clips 字段

**注意**：实际视频生成需要在可灵/即梦/Runway等工具中执行。输出「生视频执行清单」供用户操作。

**完成后**：更新 status。

### Stage 6：剪辑节奏

加载 `.workbuddy/skills/ai-video-editing/SKILL.md`

**要做的事**：
- 读取 clips 数据
- 生成粗剪时间线：入点/出点/转场/节奏
- 按3-5-15-40网格调整镜头时长
- 输出字幕表、音效标注、导出参数
- 写入 pipeline.json → timeline 字段

**完成后**：更新 status。

### Stage 7：声音设计

加载 `.workbuddy/skills/ai-sound-design/SKILL.md`

**要做的事**：
- 读取 timeline 和剧本
- 按情绪→BGM速配表推荐BGM（剪映搜索关键词）
- 按4秒法则输出音效清单
- 输出AI配音方案（角色→音色）
- 写入 pipeline.json → sound 字段

**完成后**：更新 status。

### Stage 8：发布运营

加载 `.workbuddy/skills/ai-publishing/SKILL.md`

**要做的事**：
- 生成3版标题（A/B/C测试）
- 设计封面（选第一帧 + 3-5字）
- 推荐标签（三级体系）
- 推荐发布时间
- 输出多平台分发策略
- 写入 pipeline.json → publish 字段

**完成后**：更新 status → completed。总结全链路输出。

---

## 使用规则

1. **按顺序执行，不跳过**。前一个阶段完成才能进入下一个。
2. **每阶段在回复中展示进度**：`[Stage 2/8] 编剧写作中...`
3. **使用共享数据文件 pipeline.json** 传递中间结果。
4. **如果某个阶段依赖的工具不可用**（如ImageGen），输出操作清单让用户手动执行。
5. **每完成一个阶段，更新 pipeline.json 的 status**。
6. **全流程完成后**：总结产出清单，给出可操作建议。

---

## 用户可选参数

| 参数 | 说明 | 示例 |
|------|------|------|
| 题材 | 短剧类型 | 都市逆袭、古风仙侠、甜宠、悬疑 |
| 风格 | 导演视觉 | 王家卫、韦斯安德森、末世科幻 |
| 时长 | 成品时长 | 1分钟、2分钟、15镜 |
| 热点 | 蹭的具体热点 | 某热搜话题、某流行梗 |
| 工具链 | 生图/生视频工具 | 平民（即梦/可灵）、精品（Runway） |
| 角色 | 角色数量/性别/年龄 | 女主28岁职场、男主35岁总裁 |

---

## 完整项目输出

```
projects/{project_id}/
├── pipeline.json       # 全链路数据（可从任意站断点续跑）
├── script.md           # 完整剧本
├── images/             # 分镜图
├── video/              # 视频片段
├── timeline.md         # 剪辑时间线
├── sound_plan.md       # 声音方案
└── publish_plan.md     # 发布方案
```

---

> 本Skill由女娲方法论生成，是AI短剧工厂的一键总控调度中心。9站全线通车。
