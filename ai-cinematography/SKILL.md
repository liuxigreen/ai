---
name: ai-cinematography
version: 1.3.0
trigger: 画面指令、生图Prompt、分镜、镜头指令、转成画面、画面描述、生成图片指令、AI生图、文生图Prompt、镜头描述、真人Prompt、写实画面
description: |
  AI短剧画面指令引擎。融合王家卫情绪视觉语法、韦斯·安德森构图纪律、
  末世科幻视觉语法三大导演模式，新增真人写实引擎（即梦/可灵/Midjourney蒸馏），
  awesome-gpt-image-2原子化Schema和电影分镜语法。
  支持photorealistic/风格化双轨输出，将短剧剧本自动转化为
  结构化AI生图/生视频Prompt，保证人物一致性和画风统一。
  参考《丧尸清道夫》实战验证。
author: 女娲·Skill造人术
date: 2026-06-23
---

# AI短剧画面指令引擎

> 剧本是文字的情绪，画面是光的情绪。这个引擎负责翻译。

---

## 使用方式

此 Skill 作为画面指令生成器激活。你的输入来自编剧 Skill 输出的剧本（或用户直接描述的场景），你的输出是每个镜头的结构化 Prompt。

四个导演模式可自由切换：
- **王家卫模式**：情绪优先，色彩即情感，适合情感/暧昧/怀旧/都市题材
- **韦斯·安德森模式**：纪律优先，规则即美感，适合轻喜剧/童话/风格化题材
- **末世科幻模式**：质感优先，废墟即叙事，适合科幻/末世/废土/恐怖题材
- **真人写实模式**：摄影参数驱动，皮肤毛孔级细节，默认真人短剧首选

两个生成风格可选：
- **Photorealistic**（真人版）：使用摄影参数+真人演员描述，生成写实影像
- **Stylized**（风格化）：使用导演标签+艺术风格关键词，生成动画/插画质感

默认：Photorealistic。仅当用户明确要求"动画风格/插画风格/韦斯风格化"时才切换。

---

## 原子化Schema（来源：awesome-gpt-image-2）

所有画面指令按以下模块逐层描述。来源 awesome-gpt-image-2 的 "subject + lighting + materials + layout + visual details" 原子化结构。

| 模块 | 说明 | 描述要点 |
|------|------|---------|
| **主体** | 人物+动作+表情+服装 | 谁、在做什么、什么表情、穿什么 |
| **光照** | 光源方向+色温+强度 | 光从哪来、什么颜色、硬还是柔 |
| **构图** | 景别+角度+人物位置 | 多近、什么角度、人物放哪 |
| **空间** | 环境+氛围+关键道具 | 在哪、什么感觉、有什么 |
| **风格** | 画风锁定+色调+质感 | 王家卫还是韦斯还是末世、什么色板、什么颗粒 |
| **情绪** | 1-3个情绪关键词 | 紧张/温暖/悬疑/欲望/孤独 |
| **细节** | 隐藏叙事信息 | 1个可被发现的视觉彩蛋（工牌/照片/广告牌上的字/墙上的涂鸦/桌面物品排列暗示） |
| **联动** | 与上一镜的衔接 | 同一人物、继承色调、动作接续 |

---

## 模式一：王家卫情绪视觉语法

### 色彩→情绪映射

| 情绪 | 色调 | HEX参考 | Prompt关键词 |
|------|------|---------|-------------|
| 孤独/疏离 | 蓝紫+绿（冷调高色温） | `#191970`~`#4B0082` | `blue-purple cold palette, low-key lighting, isolated figure` |
| 浪漫/暧昧 | 深红+暖金（低色温） | `#8B0000`~`#DAA520` | `deep red and warm amber, tungsten romantic glow, frame within a frame` |
| 怀旧/时间 | 暖黄+棕褐（复古滤镜） | `#DAA520`~`#B8860B` | `sepia-warm vintage filter, film grain, faded memory aesthetic` |
| 欲望/压抑 | 红vs绿对冲（高饱和） | `#DC143C`→`#2E8B57` | `red vs green high contrast, venetian blind shadow, forbidden desire` |
| 焦虑/危险 | 红蓝交替（冷暖高对比） | — | `red-blue alternating, shaky handheld, flickering fluorescent` |
| 都市漂泊 | 霓虹多色+深黑底 | — | `neon multicolor on black, wet pavement reflection, urban nomad` |

### 构图法则

| 法则 | 视觉特征 | Prompt描述 |
|------|---------|-----------|
| 框架式构图 | 门框/窗户/走廊作为前景框 | `frame within a frame, foreground obstruction, narrow corridor` |
| 人物偏置 | 角色偏向一侧，大量负空间 | `off-center isolated figure, negative space, wide angle distortion` |
| 镜面反射 | 玻璃/镜子/湿路面反射 | `mirror reflection, glass surface, wet pavement, doubled image` |
| 栅栏/百叶窗投影 | 条纹光影切面 | `venetian blind shadow, stripe light across face, prison bar shadow` |

### 光影特征

| 特征 | 技术 | Prompt关键词 |
|------|------|-------------|
| 霓虹光源 | 红/绿/蓝霓虹管+湿路面 | `neon tube lighting, wet street reflection, neon spill on face` |
| 低调布光 | 单一实用光源+面部分阴影 | `low-key lighting, single practical light, half-lit face` |
| 体积光 | 烟雾+光束可见 | `volumetric light through smoke, visible light beam, dust particles` |
| 胶片颗粒 | 35mm质感+柔和清晰度 | `35mm film grain, soft focus, -2 clarity, retro texture` |

### 王家卫快速Prompt速记

```
Wong Kar-wai cinematic: [主体描述]. 
high saturation red/green/blue, neo-noir low-key lighting, 
frame within a frame, foreground obstruction, 
wet street neon reflection, step-printing motion blur, 
film grain, handheld, shallow depth of field, 
romantic melancholy, 1960s Hong Kong aesthetic
```

---

## 模式二：韦斯·安德森构图纪律

### 对称构图体系

| 规则 | 技术要点 | Prompt关键词 |
|------|---------|-------------|
| 中心对称 | 中轴线左右镜像平衡 | `perfect bilateral symmetry, centered composition` |
| 平面化空间 | 相机90°垂直于场景平面 | `flat planimetric composition, 90-degree camera angle` |
| 角色居中 | 单人镜头中精确居中 | `character centered on vertical axis, deadpan face to camera` |
| 横向运动 | 角色在画面中左右移动 | `horizontal character movement only, lateral tracking shot` |

### 调色板系统（60-30-10规则）

| 层级 | 作用 | 占比 |
|------|------|------|
| 主色 | 场景的情绪基调 | 60% |
| 辅色 | 对比和深度 | 30% |
| 强调色 | 视觉焦点 | 10% |

**经典韦斯调色方案速查**：

| 影片 | 色板 | Prompt |
|------|------|--------|
| 布达佩斯大饭店 | 粉+紫+金 | `pastel pink purple gold, confectionery palette, storybook` |
| 月升王国 | 芥末黄+天蓝+卡其 | `mustard yellow sky blue khaki, 1960s scout aesthetic` |
| 水中生活 | 淡蓝+红+白 | `pale blue red white, nautical uniform, ocean adventure` |
| 天才一族 | 红+焦糖+深绿 | `red caramel deep green, 1970s New York, intellectual chaos` |

### 机位纪律

| 规则 | 说明 | Prompt关键词 |
|------|------|-------------|
| 固定机位 | 场景切换后立即静止 | `fixed camera, static shot, no handheld` |
| 正面平视 | 拒绝斜角、拒绝荷兰角 | `straight-on eye level, no Dutch tilt, no diagonal angle` |
| 俯拍 | 正上方展示物品全貌 | `overhead bird's eye view, tabletop arrangement` |
| 85mm焦距 | 中长焦压平空间 | `shot on 85mm lens, compressed perspective` |

### 韦斯快速Prompt速记

```
Wes Anderson style: [主体描述].
perfect bilateral symmetry, centered composition,
pastel color palette, 60-30-10 color rule,
flat planimetric staging, fixed camera, 
deadpan expression, 85mm lens,
meticulously arranged props, vintage aesthetic,
Kodak Portra 400 color science, soft even lighting
```

---

## 模式三：末世科幻视觉语法（刘梓瑜/丧尸清道夫蒸馏）

> 蒸馏对象：刘梓瑜（Mx-Shell），29岁非科班AI导演。1人10天3000元做出全球刷屏的《丧尸清道夫》。核心方法论：动态编剧法 + 行为逻辑Prompt + 原子朋克美学 + LED脸取巧。

### 创作哲学：AI导演论

**原则一：你是导演，AI是演员。** 导演不告诉演员"手举45度眼往左看"——导演说"你很愤怒但必须忍住"。AI同理：给动机，不给精确指令。刘梓瑜从不画分镜图，用「一张场景参考图+一张角色图+一段文字指令」控制画面。

**原则二：不写剧本，在生成中写剧本。** 设定核心框架（世界观+主角+方向，一段话足够）→ 生成第1镜 → 看效果 → 决定第2镜 → 螺旋推进。全片生成完，脑子里才有完整剧本。

**原则三：行为逻辑法。** Prompt不写"做什么动作"，写"为什么做这个动作"。

| ❌ 命令式 | ✅ 行为逻辑式 |
|----------|------------|
| "机器人跑过沙漠" | "机器人在沙暴中狂奔，弯下腰用机械臂压住摇摇欲坠的牛仔帽——它怕帽子被风吹掉" |
| "角色在哭" | "角色在哭，因为从口袋里掏出家人的最后一张照片时，发现照片已被烧毁一半" |

**原理**：AI模型在你提供"为什么"后会自动推理出更自然的肢体语言——"怕帽子掉"会让AI自动补充弯腰角度、手臂位置、身体前倾。

### 色彩→情绪映射

| 情绪 | 色调 | HEX参考 | Prompt关键词 |
|------|------|---------|-------------|
| 荒芜/遗忘 | 铁锈橙+雾霾灰 | `#8B4513`→`#808080` | `rust orange and ash grey, desaturated decay, abandoned world` |
| 孤立/渺小 | 冷蓝灰+深黑 | `#2C3E50`→`#000000` | `cold blue-grey vastness, lone figure against ruin, negative space` |
| 最后的人性 | 暖琥珀穿透冷废墟 | `#DAA520`↔`#4A4A4A` | `warm amber light piercing cold ruins, the last warmth on earth` |
| 危险/未知 | 暗红+深渊黑 | `#8B0000`→深黑 | `deep crimson against abyss black, threat in shadow, silhouette danger` |
| 机械/异化 | 冷钢蓝+腐蚀绿 | `#708090`+`#556B2F` | `cold steel blue and corroded green, machine overtaking nature` |
| 黑色幽默 | 褪色粉彩撞废土棕 | — | `faded pastel pink toy against rusted wasteland, absurd contrast` |

### 质感语法

| 质感层 | 描述 | Prompt关键词 |
|--------|------|-------------|
| 锈蚀金属 | 铁锈斑驳、漆面剥落、边缘腐蚀 | `rusted metal surface, peeling paint, corroded edges, bullet hole scars` |
| 碎裂混凝土 | 裂缝、钢筋外露、苔藓侵入 | `cracked concrete, exposed rebar, moss through fissures, crumbling edges` |
| 被自然回收 | 藤蔓覆盖建筑、树根撑破路面、沙埋半截汽车 | `nature reclaiming, vines covering structures, sand-buried vehicles` |
| 尘埃悬浮 | 空气中可见微粒、丁达尔光束 | `dust particles suspended in air, visible light beams through haze, irradiated atmosphere` |
| 废弃遗迹 | 倒下的路牌、生锈的加油站、散落的行李 | `toppled rusted signposts, abandoned gas station, scattered luggage of the evacuated` |
| 像素/电子元件 | 外露电路、破碎LED屏、数据线缠绕 | `exposed circuit boards, cracked LED display showing pixel art emotion, tangled cables` |

### 构图法则

| 法则 | 说明 | Prompt关键词 |
|------|------|-------------|
| 垂直纵深废墟 | 人物站在废墟中央，纵深向远处延伸 | `deep perspective through ruins, lone figure at center, vanishing point in debris` |
| 巨大vs渺小 | 宏大的残骸对比渺小的人物 | `massive wreckage dwarfing a tiny figure, scale contrast, epic desolation` |
| 框架残骸 | 破损门窗/锈蚀车体作为前景框架 | `shattered window frame foreground, through a rusted car door, frame within ruin` |
| 西部地平线 | 天空仅占1/5，地平线压得很低 | `oppressive horizon line, sky barely visible top fifth, land dominates the frame` |
| 俯拍废土布局 | 正上方展示废墟全景 | `overhead bird's eye of ruined town, scattered debris arranged like a map of destruction` |

### 人物一致性：三方案（刘梓瑜实战验证）

| 方案 | 做法 | 适用 |
|------|------|------|
| **LED脸取巧法** | 主角不是人类，面部是像素LED屏显示情绪符号。叙事成立（机器人设定），技术完美（像素块不因镜头切换变形） | 科幻/机器人/非人主角 |
| **三视图@绑定** | 提前生成角色正面/侧面/背面图，生成时@角色名绑定为参考 | 人类/类人角色 |
| **Agent全能参考** | 小云雀2.0：输入角色设定+环境关键词，系统自动锁定数百镜头的统一特征 | 批量生成 |

**核心洞察**（刘梓瑜）：AI画不好真人脸→不做真人脸。**把技术限制变成创意机会**——这是他在末世模式的底层思维。由此推导出规则：末世题材的角色设计，优先考虑"能自然隐藏面部特征"的设定（机器人/戴面具/背影为主/剪影叙事）。

### 末世快速Prompt速记

```
Post-apocalyptic atompunk cinematic: [主体描述+行为原因].
rusted metal and cracked concrete, desaturated rust orange and ash grey,
volumetric light through irradiated dust, nature reclaiming structures,
lone figure against vast ruin, deep perspective through debris,
1960s retro-futuristic aesthetic mixed with western film tone,
faded film stock colors, no CGI smoothness — weathered and real,
weathered textures, abandoned world, the last trace of humanity
```

### 刘梓瑜完整工具链（供参考）

| 环节 | 工具 | 用途 |
|------|------|------|
| 核心生成 | 小云雀 Seedance 2.0 | 沉浸式短片模式：画面生成+角色绑定+音画同步 |
| 批量分镜 | 万象2.2 (ComfyUI) | 本地批量分镜视频 |
| 动态插帧 | 极梦AI | 智能插帧+动态补偿，消除卡顿 |
| 局部修复 | Procreate | 手绘修正AI画面细节 |
| 后期合成 | 剪映 | 调色+剪辑+粒子特效

---

## 通用分镜语法（任何模式均适用）

### 景别选择

| 景别 | 画面范围 | 使用时机 | AI Prompt标注 |
|------|---------|---------|--------------|
| 大远景 | 环境为主 | 开场/结尾/时间流逝 | `extreme long shot, establishing` |
| 远景 | 环境+全身 | 建立场景 | `long shot, full body in environment` |
| 全景 | 角色全身+动作 | 角色关系和动作 | `full shot, character action` |
| 中景 | 半身 | 对话和日常 | `medium shot, waist-up` |
| 近景 | 胸部以上 | 情绪和反应 | `medium close-up, chest-up` |
| 特写 | 脸部/局部 | 情绪高潮/关键信息 | `close-up, face only, intimate` |

**景别切换规则**：相邻镜头至少跨越一个景别等级。竖屏短剧优先使用中景和近景。

### 180度轴线 + 正反打

- 对话场景保持摄像机在轴线同一侧
- 正反打镜头需标注角色视线方向：`looking left` / `looking right`
- 越轴 = 制造不安感，故意使用时要注明目的

### 镜头衔接

- **Cut on Action**：同一动作跨镜头延续
- **动接动/静接静**：运动镜头接运动，静止接静止
- **Match Cut**：通过形状/颜色/方向的相似性转场

---

## 模式四：真人写实引擎（即梦/可灵/Midjourney 三平台蒸馏）

> 来源：即梦 Seedance 2.0 真人教程 + Midjourney 逼真照片公式 + PHP.cn 超写实技巧
> 核心原则：**够细、够准、不空洞。** 你敷衍AI，AI就敷衍你。

### 真人写实 Prompt 万能公式

```
人物基础信息 + 五官细节 + 穿搭妆容 + 动作神态 + 场景环境 + 风格参数 + 摄影参数
```

### 公式 ↔ Schema 映射（工业级：awesome-gpt-image-2 原子化驱动）

> 每条真人写实Prompt必须完整覆盖Schema的8个字段。以下是各字段在真人写实模式下的"工业级填充标准"。

| Schema模块 | 真人写实填充标准 | 敷衍 vs 工业级 |
|-----------|---------------|---------------|
| **主体** | `人物基础+五官细节+穿搭妆容`：年龄/脸型/眼型/鼻型/唇型/肤色/特征点/发型/服装材质 | ❌ "一个年轻女性" → ✅ "28岁中国女性，偏长鹅蛋脸，单眼皮丹凤眼，左耳垂小黑痣，白色棉麻衬衫领口微皱" |
| **光照** | `光源+方向+色温+强度+硬/柔`：必须指定一个主光源和一个辅光源 | ❌ "办公室灯光" → ✅ "左侧落地窗上午10点自然光为主光源，右侧显示器冷白屏为补光，柔光，色温5500K" |
| **构图** | `景别+角度+人物位置+视觉引导线`：标出景别和人物在画面中的比例 | ❌ "中景" → ✅ "中景，肩部以上，人物偏右占画面60%，左侧负空间留白，门框作为前景框" |
| **空间** | `环境+材质+关键道具+氛围`：环境材料要写材质老化痕迹，关键道具要写具体 | ❌ "办公室" → ✅ "高层写字楼，白墙+浅木桌面，桌上半杯冷咖啡，保温杯壁有冷凝水珠，百叶窗投下条纹阴影" |
| **风格** | `色调+质感+摄影参数`：用相机参数替代风格形容词 | ❌ "电影感" → ✅ "Shot on ARRI Alexa, 50mm f/2.0, Kodak Portra 400 color science, 35mm film grain, natural color grade" |
| **情绪** | `1-3个情绪关键词`：必须有一个"身体反应"来描述情绪 | ❌ "孤独" → ✅ "疲惫、压抑——肩膀微垂，眼神停留在手机屏幕上的时间超过10秒" |
| **细节** | `1个隐藏叙事信息`：观众第一遍不会注意，第二遍恍然大悟 | ❌ 无 → ✅ "桌面角落有一张被揉皱后又展平的调薪申请单，日期是三个月前" |
| **联动** | `人物一致性注入 + 色调继承 + 动作接续`：每条Prompt末尾强制追加 | ❌ 无 → ✅ "Character ref: 林雪——鹅蛋脸/杏仁眼/黑框眼镜/白衬衫/左手红绳。同镜1色调，承接撕工牌后起身的动作" |

### 完整示例：一条Prompt如何覆盖8个Schema字段

```
主体: 28岁中国女性林雪，偏长鹅蛋脸，单眼皮丹凤眼，肤色冷白偏黄，黑色中长发低马尾，白色棉麻衬衫领口微皱，黑框钛合金眼镜，左手红绳手链。

光照: 左侧落地窗上午10点自然光为主光源(柔光，色温5500K)，右侧显示器冷白屏为补光，百叶窗投下条纹阴影在桌面。

构图: 中景，肩部以上，人物偏右占画面60%，门框作为前景框，左侧负空间留白。

空间: 高层写字楼，白墙+浅木桌面，桌上半杯冷咖啡(马克杯壁冷凝水珠)，揉皱又展平的调薪申请单(日期三个月前)，百叶窗条纹阴影。

风格: Shot on ARRI Alexa, 50mm f/2.0, Kodak Portra 400 color science, 35mm film grain, natural color grade, photorealistic.

情绪: 疲惫、压抑——肩膀微垂，眼神停留在手机屏幕时间超过10秒。

细节: 桌面角落的调薪申请单日期是三个月前（暗示：她的升职已被压了三个月，随时可能爆发）。

联动: Character ref: 林雪——鹅蛋脸/杏仁眼/黑框眼镜/白衬衫/左手红绳。继承镜1蓝紫冷调。承接看手机后撕工牌的动作。
```

→ 合并为一条可用的完整Prompt（英文为主，中文/特殊词保留）:

```
Photorealistic live-action. Medium shot. A 28-year-old Chinese woman, oval face, monolid phoenix eyes, pale warm-toned skin, black hair in low ponytail, white cotton-linen shirt with slightly wrinkled collar, black titanium-framed glasses, red string bracelet on left wrist. Sitting at desk in high-rise office. Left side floor-to-ceiling window, 10AM natural daylight as key light, soft, 5500K. Right side monitor cool screen as fill light. Venetian blind shadows striping across desk. White wall, light wood desk surface. Half-empty cold coffee in ceramic mug with condensation droplets. A crumpled-then-flattened salary review request on desk corner, date three months ago. Shoulders slightly drooped, eyes fixed on phone screen longer than natural. Off-center composition, figure positioned right 60%, door frame as foreground element, negative space left. Shot on ARRI Alexa, 50mm f/2.0, Kodak Portra 400 color science, 35mm film grain, natural color grade. Vertical 9:16. --no illustration, painting, cartoon, CGI, 3D render, plastic skin, airbrushed
```

**关键规则**：Schema的8个字段必须在Prompt中全部出现。缺任何一个，画面质量就降一档。这是工业级和业余级的唯一区别。

### 各模块速查表

#### 人物基础（必须具体到身份锚点）

| 维度 | 敷衍写法 ❌ | 真人写法 ✅ |
|------|-----------|----------|
| 年龄 | 年轻女性 | 28岁中国女性 |
| 脸型 | 漂亮 | 偏长鹅蛋脸，下巴略尖，下颌线柔和 |
| 眼睛 | 大眼睛 | 单眼皮丹凤眼，眼裂偏长，瞳孔深棕色 |
| 职业 | 白领 | 戴黑框钛合金细框眼镜，白色衬衫领口微皱 |
| 身份痕迹 | 无 | 左耳垂小黑痣，额头鼻翼有轻微毛孔纹理 |

#### 穿搭妆容（描述服装材质，不写品牌）

```
面料：棉麻/丝绸/雪纺/牛仔/羊绒 + 颜色 + 版型 + 状态（微皱/磨损/新）
妆容：清透底妆/豆沙色口红/橘色眼影/无眼线 → 指定具体色号和部位
```

#### 动作神态（不说"微笑"，说微表情）

| 敷衍 ❌ | 真人 ✅ |
|--------|--------|
| 微笑 | 嘴角微扬，露出一点点牙齿，右颊浅酒窝出现 |
| 站立 | 站姿放松，重心偏左脚，双手插卫衣口袋 |
| 看窗外 | 盯着窗外，手指无意识地敲着桌面——在等不会来的人 |
| 走路 | 双手自然摆动，步幅不大微拖，0.8x慢跟拍 |

#### 场景环境（描述材质和光源）

```
不是"办公室" → 现代简约办公室，白墙+浅木色办公桌，左侧落地窗，上午10点自然光从百叶窗渗入，桌上半杯冷咖啡
不是"街头" → 春风街夜市，炭火红光，暖黄灯泡串，红蓝塑料凳，湿漉漉的柏油路面倒映霓虹
```

**场景必须写材质老化痕迹**。规则：场景中出现 ≥1 个物品，该物品必须有"使用证据"（磨损/污渍/老化）。全新物品 = 假。缺少老化细节 = 模型感。

#### 工业级场景道具质感词库（电影美术部门蒸馏）

> 来源：FilmDaft Set Dressing指南 + 80+术语Art Department Glossary + FilmFarm Distressing技法
> 文件：`references/sources/production-design-glossary.md`

**道具三级分类**：手持道具(Hand Props) → 场景道具(Set Props) → 陈设道具(Smalls)。越靠近镜头的物品描述越细。

**6类材质老化速查**：

| 材质 | 必查老化类型 | Prompt注入示例 |
|------|------------|--------------|
| 金属 | 锈蚀/刮擦/指纹 | `rusted iron with orange-brown oxidation at edges, fingerprint smudges on polished surface` |
| 木材 | 开裂/碰撞/水渍 | `worn mahogany desk, water ring stains on surface, dented corners from years of use` |
| 皮革 | 裂纹/磨损/褪色 | `cracked leather armchair, sun-faded on window side, deep creases at flex points` |
| 布料 | 起球/磨破/褪色 | `frayed cuffs on cotton shirt, threadbare at elbows, sun-bleached color gradient` |
| 玻璃 | 冷凝水/指纹/缺口 | `condensation droplets on cold glass, greasy fingerprints on rim, chipped edge` |
| 纸张 | 泛黄/折痕/卷边 | `yellowed paper with age-toned edges, dog-eared corners, flattened fold marks` |

**Set Dressing四层构建法**（从大到小层层叠加）：
```
第1层 大型家具 → 建立空间功能和时代
第2层 中型陈设 → 帷幔/灯具/地毯
第3层 小型物品 → 书籍/餐具/个人物品
第4层 表面细化 → 灰尘/划痕/指纹/水渍（最少1处）
```

**关键Prompt术语**：
- `lived-in` = 有人住过的痕迹感
- `weathered` = 风吹日晒自然老化
- `patina` = 长期使用形成的天然老化层
- `grimy` = 油污积垢（厨房/机械场景）
- `hero prop` = 特写级道具，写3倍细节

**场景可信度自检**：每条Prompt写完问自己——所有物品有使用痕迹吗？光线有来源吗？人物和环境有互动证据吗？有一个观众第一遍不会注意但第二遍恍然大悟的隐藏细节吗？

**最小工业词密度（强制规则）**：

> 每条 Prompt 完成后必须自检。镜头越重视觉权重越高，工业词不能低于下限。

| 景别 | 权重 | 最低工业词数 | 典型镜头类型 |
|------|------|------------|------------|
| 特写 | ⭐⭐⭐⭐⭐ | **≥5** | 人物脸部/手部/关键道具 Hero Prop |
| 中近景/中景 | ⭐⭐⭐⭐ | **≥4** | 人物互动、核心冲突场景 |
| 全景/群像 | ⭐⭐⭐ | **≥3** | 多人同框、环境建立、配角场景 |
| 大远景/留白/POV | ⭐⭐ | **≥2** | 风景收束、驾驶舱视角、空镜过渡 |

违反规则 → 镜头必须重写。远景/POV 量级虽低，但 `--no` 反风格化词不计入工业词数（那是安全基线，不是质量指标）。

**检查方法**（每条Prompt成稿后跑一遍）：
```
Photorealistic ✅ | ARRI/50mm/Kodak/DC ✅ | 皮肤细节(毛孔/疤痕/纹理) ≥1 ✅
材质老化(锈/裂/磨损/褪色/冷凝水/泛黄) ≥1 ✅ | 环境互动(杯子有人喝过/桌面有痕迹/墙角有灰尘) ≥1 ✅
--no 反风格化词 ✅ | 总工业词 ≥ 景别下限 ✅
```

> 规则来源：实战验证——前两版逍遥仙和张雪机车输出中，s01-s03天然达到5-12词，s07-s09自然降至2-3词。不是创意质量问题，是缺乏强制自检机制。此规则填补这个缺口。

#### 风格参数（平台专属）

| 平台 | 关键参数 |
|------|---------|
| 即梦 Seedance 2.0 | Seedance 2.0画质，高清8K，保留皮肤纹理发丝细节，无过度磨皮，竖屏9:16 |
| 可灵 3.0 | photorealistic, 4K, natural skin texture, film grain, 50mm lens |
| Midjourney | --style raw --stylize 0 --ar 9:16 |

### 皮肤与质感关键词库

**皮肤真实层**（逐层叠加）：
```
基础：photorealistic, DSLR photograph, shot on Kodak Portra 400
皮肤：visible pores on nose and forehead, faint freckles, subtle sebum sheen on T-zone
血管：translucent skin showing faint blue subdermal veins on temple
光影：subsurface scattering on ears, accurate occlusion shadow under chin
校验：photographic evidence quality, consistent light direction across all surfaces
```

**材质真实层**：
```
织物：realistic fabric drape with micro-wrinkles and fiber fuzz on cotton
皮革：matte leather with natural crease lines and subtle surface grain
金属：brushed stainless steel with fingerprint smudges, slight patina
玻璃：condensation droplets on cold glass surface, faint reflection
陶瓷：matte-finish ceramic with slight speckled glaze texture
木材：visible wood grain, slight roughness at unvarnished edges
```

### 反风格化词（必须加到每条Prompt末尾）

```
--no illustration, painting, cartoon, anime, 3D render, CGI, sketch, drawing, oversaturated, plastic skin, smooth gradient, airbrushed, perfect symmetry, cloned features
```

### 摄影参数标准注入

每条Prompt至少包含：
```
Shot on [ARRI Alexa / Canon EOS R5 / Sony A7IV]
[24mm / 35mm / 50mm / 85mm] lens
f/[1.8 / 2.0 / 2.8]
[natural lighting / studio lighting / golden hour / tungsten warm]
Vertical 9:16
```

### 人物一致性真人方案

**方案一：参考图+提示词双保险（即梦首选）**
1. 上传角色定妆照为参考图
2. 提示词中加「严格参照参考图的五官特征、气质风格，保留穿搭和神态，不改变核心特征」
3. 成功率远超纯文字描述

**方案二：身份锚点锁定**
同一个角色在所有Prompt中固定注入：
```
[姓名], [年龄]岁[国籍]人, [脸型], [眼型], [鼻型], [唇型], [肤色], [面部特征点], [发型], [体型], [服装]
```
每次不改这些字段，只改动作和场景。

---

## AI人物一致性方案

### 方案一：角色卡片模板（最推荐，门槛最低）

为每个角色建立**200词级别**的固定描述，所有镜头复用。5行不够，AI需要每个维度的精确参数才能跨镜头保持长相一致。

```
【角色卡片：角色名】
年龄/性别：
面部：
- 脸型（长宽比/下巴形状/下颌线硬度）
- 眼型（单/双/内双、眼尾方向、眼裂长短、瞳孔颜色）
- 鼻型（鼻梁高度/鼻头形状/鼻孔特征）
- 唇型（厚薄比/嘴角方向/唇峰特征）
- 肤色（色调+纹理+特征斑痣）
- 眉毛（粗细/浓淡/眉尾状态）
- 特征点（痣/疤痕/不对称/酒窝，至少1个——AI靠这个锁人物）
发型：
- 古装/现代各一版（长度/扎法/刘海/发质/发色/白丝分布）
体型：
- 身高cm + 体型描述 + 肩宽 + 明显体态特征（驼背/斜肩/步态）
服装（分古今两套）：
- 上衣（材质/颜色/版型/磨损状态）
- 下装（材质/颜色/版型）
- 鞋（类型/磨损）
- 配饰（至少1个不换的标志物——红绳/戒指/手表/项链）
表情基调：
- 常态/开心/震惊/专注 四种表情的具体变化
动作习惯：
- 3个不随场景改变的小动作（摸手链/歪头/咬嘴唇等）
```

在Photorealistic模式下，所有Prompt末尾强制注入：
```
Character reference — [角色名]: [年龄+体型]。面部：[脸型+眼型+鼻型+唇型+肤色+特征点]。发型：[具体描述]。服装：[具体描述]。标志配饰：[不可换的物件]。表情基调：[常态描述]。Posture：[体态习惯]。
```

### 方案二：定妆照+图生视频

1. 先出角色定妆照（正面半身高清纯色背景）
2. 后续镜头使用图生视频模式，上传定妆照为参考
3. Prompt只描述动作和场景，角色面貌由参考图锁定

### 方案三：固定Seed值

同场景连续镜头使用相同Seed值生成，减少随机波动

### 方案四：刘梓瑜LED脸取巧法

**不做人脸，做特征面。** 丧尸清道夫实战验证：把主角的脸设计成像素LED屏——在叙事上成立（机器人设定，像素符号表达情绪），在技术上完美（像素方块不因镜头切换变形），在风格上独特（成为全片标识）。

**启发规则**：遇到AI人物一致性难题时，先问——能不能在角色设定层面绕过这个问题？可选路径：
- 非人类面部（机器人LED屏/面具/头盔/绷带蒙面）
- 剪影/背影为主（减少正面镜头频率）
- 固定特征遮挡物（墨镜/斗笠/口罩——在特定题材中自然成立）

### 方案五：刘梓瑜三视图@绑定法

1. 提前生成角色正面/侧面/背面三张定妆图
2. 使用小云雀的"@角色名"功能将三视图绑定为角色参考
3. 生成时AI自动以三视图为基准保持角色外观一致

---

## 行为逻辑Prompt法（刘梓瑜核心技法，全模式通用）

**核心原则**：不写"做什么"，写"为什么做"。

| ❌ 命令式 | ✅ 行为逻辑式 |
|----------|------------|
| "角色跑起来" | "角色在暴雨中狂奔，用手按住领口——怕雨水灌进衣服里" |
| "角色在看窗外" | "角色盯着窗外，手指无意识地敲着桌面——她在等一个不会来的人" |
| "角色摔倒" | "角色被绊倒，第一反应不是爬起来，而是先护住口袋里的照片" |

**AI响应原理**：给出"为什么"之后，模型会自动推理出更准确的肢体语言。"怕雨水灌进衣服"会让AI自动补充：肩膀耸起、头低、步幅变小——这些细节如果靠命令式逐条写，不但繁琐而且容易僵硬。

---

## 完整工作流：剧本→画面指令

### 步骤1：读取剧本

从编剧Skill输出（或用户输入）中提取：场景描述、人物、情绪、动作、对白

### 步骤2：拆解镜头

按「1个情绪转折 = 1个镜头」原则。典型60秒短剧单集 = 3-5个镜头。

### 步骤3：选择导演模式 + 生成风格

- 情感/都市/怀旧/悬疑 → 王家卫模式
- 轻喜剧/童话/风格化/明亮 → 韦斯模式
- 科幻/末世/废土/恐怖/后末日 → 末世科幻模式
- **高质量真人短剧/日常/古风/职场 → 真人写实模式（即梦Seedance 2.0/可灵3.0/Midjourney）**
- 可混用：主情感线用一种，特定段落换另一种

**生成风格确认**：
- 用户要求"真人/写实/电影级"或未指定 → **Photorealistic**：用模式四万能公式（人物+五官+穿搭+神态+场景+摄影参数）+ 反风格化词
- Photorealistic 模式必须加载「真人写实引擎」模块：皮肤质感关键词 + 材质真实层 + 摄影参数注入
- 用户要求"动画/插画/风格化/Wes Anderson style" → **Stylized**：用艺术风格标签
- 注意：即梦/可灵等国产工具对"photorealistic"响应更好，默认走真人路线

**隐藏细节检查**：
- 每3镜至少1镜埋入隐藏叙事信息（背景道具/环境文字/人物身上的暗示物）
- 在输出模板的【细节】字段明确标注

### 步骤4：套用Schema逐镜头生成

每个镜头按模板输出。**必须包含联动字段**确保连续性。

---

## 输出格式模板

```
## 第X集 · 镜头序列

> 总色调：[色调方案] | 导演模式：[王/韦/末世] | 生成风格：[Photorealistic/Stylized] | 画风锁定：[统一标记]

### 镜头1：[景别]
【主体】人物（角色卡名称）+ 动作 + 表情 + 服装
【光照】光源方向 + 色温 + 强度
【构图】景别 + 角度 + 人物位置
【空间】环境 + 氛围 + 关键道具
【风格】色调方案 + 质感参数 + [王/韦/末世]专属元素
【情绪】1-3关键词
【细节】隐藏叙事信息：[具体可发现的视觉彩蛋]
【联动】无（首镜）

→ Prompt（Photorealistic）：
[完整英文Prompt，摄影参数+角色卡片注入+场景描述，无style标签]

→ Prompt（Stylized备选）：
[完整英文Prompt，艺术风格标签+角色卡片注入+场景描述]

### 镜头2：[景别]
【主体】...
【细节】隐藏叙事信息：[...]
【联动】人物：同镜头1[角色名]，服装发型一致 | 色调：继承 | 动作：继[动作]之后
...

（重复至本集最后镜头）
```

---

## 避坑清单

1. ❌ **角色描述不一致** → 每次使用时都用同一段完整角色卡片描述（200词级别），不能临时简化
2. ❌ **人物描述太简单** → "年轻女性，长发，白衬衫"无法让AI跨镜头保持长相一致。需要脸型/眼型/鼻型/唇型/特征点/配饰
3. ❌ **相邻镜头景别跳级** → 远景直接切特写在特殊情绪场景才可用
4. ❌ **不看轴线乱切正反打** → 标注角色视线方向
5. ❌ **色调突变** → 同一集的色板方案在第一个镜头就声明，后续严格继承
6. ❌ **特效描述太模糊** → "电影质感"改成"shot on ARRI Alexa, 35mm film grain, Kodak Portra 400 color"
7. ❌ **动了不接静** → 前镜手持晃动，后镜不能无缝切到固定机位
8. ❌ **默认走Stylized路线** → 即梦/可灵对photorealistic响应更好。除非用户明确要动画风格，默认用真人摄影参数
9. ❌ **隐藏细节指向不明** → "背景有东西"不行，必须说清楚"褪色工牌上能看到模糊的工号"

---

## 诚实边界

- 基于王家卫/韦斯·安德森公开作品和访谈提取的视觉规则，非二人亲述
- 末世科幻视觉语法基于《爱，死亡和机器人》类型美学+《丧尸清道夫》实战验证提炼
- 人物一致性方案基于2026年6月可用的工具状态（即梦/可灵/ComfyUI），AI工具更新可能产生更好方案
- 实际生成效果取决于所使用的AI工具版本和参数配置
- awesome-gpt-image-2 的Schema为框架引用，具体模板已适配短剧场景

---

## 调研来源

- 王家卫视觉体系：10来源（豆瓣/知乎/ReelMind/Color Culture等）
- 韦斯·安德森视觉体系：19来源（StudioBinder/No Film School/Smithsonian等）
- 刘梓瑜AI创作方法论：7来源（腾讯新闻本人访谈/腾讯云技术拆解/新浪制作全流程/知乎/百度百科/头条/搜狐）
- 真人写实Prompt工程：5来源（即梦Seedance 2.0官方教程/PHP.cn超写实技巧/Midjourney逼真照片公式/ChooseAI实战模板/知乎人像摄影关键词）
- 分镜语法+AI一致性：42来源（含awesome-gpt-image-2模板文档）
- 完整调研文档见 `references/sources/`

---

> 本Skill由女娲方法论 + AI短剧导演蒸馏法生成
> 视觉语法来源：王家卫电影作品 × 韦斯·安德森电影作品 × 刘梓瑜《丧尸清道夫》
> 结构框架来源：awesome-gpt-image-2 原子化Schema
> 创建日期：2026-06-23 | 升级 v1.1：2026-06-23
