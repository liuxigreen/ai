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

## 核心原则（必须遵守）

> 🚨 **禁止使用模板数据。禁止使用 generateFakeOutput() 或任何硬编码输出。如果 Stage 1 的热点分析输出了和用户输入无关的题材，整个流水线作废，必须重跑。**

1. **每阶段必须加载对应子 SKILL.md 全文，并真正执行其方法论**。不可返回模板数据或空壳输出。
2. **用户输入贯穿始终**。热点发现必须分析用户输入的具体关键词。用户说「筷子兄弟逍遥仙，老一辈艺术家膈应人」，你就分析这个文化现象——古风+反串+AI+荒诞。不是输出一个不相干的职场故事。
3. **上游输出喂给下游**。Stage 2 读取 Stage 1 的产出，Stage 3 读取 Stage 2 的产出，以此类推。
4. **输出必须达到子 Skill 的标准格式**。编剧必须输出完整剧本（场景+对话+情绪标注），画面指令必须输出每镜8模块Prompt。
5. **每阶段先更新 pipeline.json status → running，完成后写入 output 并更新 status → done。**

**自检规则（Stage 1 完成后强制执行）**：
```
检查：hotspot.adaptation.genre 是否与用户输入的关键词相关？
例：用户输入含「逍遥仙」 → genre 应为「古风/反串/搞笑/奇幻」而非「都市逆袭」
若不一致 → 此 Stage 1 无效，重新分析
```

---

## Stage 0：环境初始化

1. 创建项目目录：`projects/{project_id}/`
2. 创建 `projects/{project_id}/pipeline.json`
3. 写入初始数据（project_id / user_input / genre / style / duration / stages 全部 pending）
4. 确认用户输入的关键信息：题材偏好？视觉风格偏好？时长？

---

## Stage 1：热点发现

**指令**：
- Read `.workbuddy/skills/hotspot-discovery/SKILL.md`
- 🚨 **先搜索，再分析**。不可跳过搜索直接编数据。
- 用 WebSearch 搜索用户输入的关键词（至少2次），获取热点背景、观众反应、相关话题
- 有高价值URL时用 WebFetch 抓取全文
- 再用四维拆解框架（情绪/冲突/人设/框架）分析搜索结果
- 分析的是用户给的**具体关键词**，不是自己编的通用热点
- 你是在分析用户给你的那个热点，不是随便编一个
- 如果用户输入是「筷子兄弟逍遥仙」，搜一下这个热点是什么（古风+反串+搞笑+AI MV），不要套我们的演示模板

**必须输出的字段**：
```json
{
  "hotspot": {
    "title": "用户输入关键词的提炼",
    "source": "热榜来源或文化现象来源",
    "lifecycle": "上升期/爆发期",
    "emotion_engine": { "core": "核心情绪", "curve": "情绪曲线" },
    "four_d": { "emotion": "...", "conflict": "...", "persona": "...", "framework": "..." },
    "adaptation": { "genre": "匹配的题材类型", "diff_angle": "与已有爆款的差异化切入点" }
  }
}
```

**完成后**：写入 pipeline.json，status → done。

---

## Stage 2：短剧编剧

**指令**：
- Read `.workbuddy/skills/short-drama-screenwriting/SKILL.md`
- 读取 Stage 1 的 hotspot.adaptation.genre 和 emotion_engine
- 用四阶段流：题材确认→结构搭建→写作执行→输出
- 必须输出**完整剧本**，不是大纲摘要

**必须输出的字段**：
```json
{
  "script": {
    "format": "15镜短片 或 80集前3集试播",
    "genre": "题材类型",
    "emotion_curve": "从0秒到结尾的情绪变化",
    "episodes": [
      {
        "ep": 1,
        "scene": "场景描述",
        "characters": ["角色1", "角色2"],
        "shots": [
          "△ 具体镜头描述（含动作/情境/对话/情绪标注）",
          "△ ..."
        ],
        "cliffhanger": "本集结尾的钩子/悬念"
      }
    ]
  }
}
```

**质量标准**：
- 每个镜头不少于1行具体描述
- 对话要写出来（除非用户指定无台词模式）
- 情绪标注必须写（疲惫/震惊/愤怒/释然等）

**完成后**：写入 pipeline.json，status → done。

---

## Stage 3：画面指令

**指令**：
- Read `.workbuddy/skills/ai-cinematography/SKILL.md`
- 读取 Stage 2 的剧本（episodes → shots）
- 根据题材和情绪选择合适的导演模式（王/韦/末世）
- 为每个镜头生成完整的7模块Prompt
- 输出角色卡片（200词级别）

**必须输出的字段**：
```json
{
  "cinematography": {
    "director_mode": "wong / anderson / apocalyptic",
    "color_palette": "色调方案 + 质感参数",
    "character_card": { "name": "...", "face": "...", "hair": "...", "build": "...", "costume": "...", "expression_base": "..." },
    "shots": [
      {
        "shot_id": "s01",
        "framing": "景别",
        "mood": "情绪词",
        "prompt": "完整的英文/中文Prompt，包含主体/光照/构图/空间/风格/情绪/联动"
      }
    ]
  }
}
```

**质量标准**：
- 每镜 Prompt 必须包含主体/光照/构图/空间/风格/情绪/联动 7个字段的信息
- 角色卡片至少10行描述
- 联动字段标注人物一致性（同一角色→服装发型一致）

**完成后**：写入 pipeline.json，status → done。

---

## Stage 4：生图执行

**指令**：
- Read `.workbuddy/skills/ai-image-generation/SKILL.md`
- 读取 Stage 3 的 shots（每个镜头的 Prompt）
- 按工具链选择（平民/精品/工业化），输出每个镜头的生图参数
- 写入 CHAR 资产库策略

**必须输出的字段**：
```json
{
  "image_gen": {
    "toolchain": "即梦 S2.0 Pro / ComfyUI / Midjourney",
    "per_shot": { "seed": "固定种子", "model": "...", "steps": "...", "cfg": "..." },
    "char_asset": { "ref_image_type": "定妆照", "seed_lock": true },
    "draw_strategy": "3S抽卡：每镜抽3张→选最稳",
    "note": "用户需在即梦/可灵中手动执行"
  }
}
```

**完成后**：写入 pipeline.json，status → done。

---

## Stage 5：生视频

**指令**：
- Read `.workbuddy/skills/ai-video-generation/SKILL.md`
- 读取 Stage 3 的 shots 和 Stage 4 的工具链选择
- 为每个镜头分配运镜类型、运动幅度、首尾帧策略

**必须输出的字段**：
```json
{
  "video_gen": {
    "tool": "可灵 3.0 / Runway / 即梦",
    "per_clip": [{ "shot_id": "s01", "camera_move": "慢推", "motion_strength": "中低档3-5", "duration": "4-6秒", "note": "首帧用分镜图" }],
    "chain": "首尾帧链策略",
    "note": "用户需在可灵/Runway中手动执行"
  }
}
```

**完成后**：写入 pipeline.json，status → done。

---

## Stage 6：剪辑节奏

**指令**：
- Read `.workbuddy/skills/ai-video-editing/SKILL.md`
- 读取 Stage 2 的剧本和 Stage 5 的视频片段参数
- 输出粗剪时间线：每段入点/出点/转场/节奏意图

**必须输出的字段**：
```json
{
  "editing": {
    "rhythm_grid": "按3-5-15-40网格标注每段节奏意图",
    "cuts": [{ "shot_id": "s01", "duration": 3.5, "transition": "hard_cut / 叠化 / 光闪", "rhythm_intent": "钩子/铺垫/反转/高潮" }],
    "subtitles": "字幕位置、字号、样式",
    "export": "平台+分辨率+帧率+码率+编码"
  }
}
```

**完成后**：写入 pipeline.json，status → done。

---

## Stage 7：声音设计

**指令**：
- Read `.workbuddy/skills/ai-sound-design/SKILL.md`
- 读取 Stage 2 的剧本和 Stage 6 的时间线
- 为每个情绪段落推荐BGM（含剪映搜索关键词）
- 为每个镜头标注需要铺的音效

**必须输出的字段**：
```json
{
  "sound": {
    "bgm": [{ "emotion": "情绪", "search": "剪映关键词", "range": "s01-s05" }],
    "sfx": [{ "shot": "s01", "keyword": "音效关键词", "type": "环境/动作/情绪/转场" }],
    "voiceover": { "tool": "剪映文本朗读", "timbre": "音色", "speed": 1.0 },
    "volume_mix": "人声-6dB / 音效-12dB / BGM-22dB"
  }
}
```

**完成后**：写入 pipeline.json，status → done。

---

## Stage 8：发布运营

**指令**：
- Read `.workbuddy/skills/ai-publishing/SKILL.md`
- 读取全链路数据
- 生成3版标题（A/B测试）、封面方案、标签、发布时间、多平台策略

**必须输出的字段**：
```json
{
  "publish": {
    "title": { "primary": "主标题", "ab_test": ["备选1", "备选2"] },
    "cover": { "frame": "选第几帧", "text": "封面大字", "style": "字体+描边" },
    "tags": ["#品类标签", "#情绪标签", "#热点标签"],
    "publish_time": "最佳时间",
    "platforms": [{ "name": "抖音/快手/B站...", "note": "适配说明" }],
    "copy": { "line1": "文案第1行", "line2": "文案第2行", "line3": "互动引导" }
  }
}
```

**完成后**：status → done。全链路完成，总结输出清单。

---

## 检查清单（每个 Stage 完成后自查）

- [ ] 输出是否参考了用户的原始输入？没有跑偏？
- [ ] 输出是否符合子 Skill 的标准格式？
- [ ] 数量够不够？（编剧至少N个镜头描述、画面指令至少N个Prompt）
- [ ] 数据是否写入了 pipeline.json？
- [ ] 如果是前几个 Stage，下游能否直接读取？

---

## 完整项目输出

```
projects/{project_id}/
├── pipeline.json       # 全链路数据
├── script.md           # 完整剧本
├── images/             # 分镜图
├── video/              # 视频片段
└── output/             # 最终发布方案
```

---

> 本Skill由女娲方法论生成，是AI短剧工厂的一键总控调度中心。9站全线通车。
