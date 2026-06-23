---
name: ai-cinematography
version: 1.2.0
trigger: 画面指令、生图Prompt、分镜、镜头指令、转成画面、画面描述、生成图片指令、AI生图、文生图Prompt、镜头描述
description: |
  AI短剧画面指令引擎。融合王家卫情绪视觉语法、韦斯·安德森构图纪律、
  末世科幻视觉语法三大导演模式，awesome-gpt-image-2原子化Schema和
  电影分镜语法。支持photorealistic/风格化双轨输出，将短剧剧本自动转化为
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

三个导演模式可自由切换：
- **王家卫模式**：情绪优先，色彩即情感，适合情感/暧昧/怀旧/都市题材
- **韦斯·安德森模式**：纪律优先，规则即美感，适合轻喜剧/童话/风格化题材
- **末世科幻模式**：质感优先，废墟即叙事，适合科幻/末世/废土/恐怖题材

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
- 可混用：主情感线用一种，特定段落换另一种

**生成风格确认**：
- 用户要求"真人/写实/电影级"或未指定 → **Photorealistic**：用摄影参数（ARRI Alexa / 50mm f/2.0 / 35mm film grain）+ 真人演员描述
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
- 分镜语法+AI一致性：42来源（含awesome-gpt-image-2模板文档）
- 完整调研文档见 `references/sources/`

---

> 本Skill由女娲方法论 + AI短剧导演蒸馏法生成
> 视觉语法来源：王家卫电影作品 × 韦斯·安德森电影作品 × 刘梓瑜《丧尸清道夫》
> 结构框架来源：awesome-gpt-image-2 原子化Schema
> 创建日期：2026-06-23 | 升级 v1.1：2026-06-23
