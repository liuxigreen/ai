# 分镜语法与AI生图：规则 - 一致性 - 模板

> 搜索时间：2026-06-23
> 用途：构建AI短剧画面指令Skill的补充参考模块

---

## Part 1: 分镜拆解规则（Shot Breakdown）

### 1.1 核心规则总结

#### 景别序列（Shot Size Sequence）

| 景别 | 英文 | 画面范围 | 适用场景 |
|------|------|----------|----------|
| 大远景 | Extreme Long Shot | 环境为主 | 开场、结尾、时间流逝 |
| 远景 | Long Shot | 环境+角色全身 | 建立场景、过渡 |
| 全景 | Full Shot | 角色全身+动作 | 角色关系和动作 |
| 中景 | Medium Shot | 半身或小范围动作 | 对话和日常动作 |
| 近景 | Medium Close-Up | 胸部以上 | 情绪和反应 |
| 特写 | Close-Up | 脸部或局部细节 | 情绪高潮、关键信息 |

**切换逻辑（景别组接原则）：**
- **不要相邻景别直接跳切**：远景→全景→中景→近景→特写的线性排列会让观众产生"跳脱感"，应跨越至少一个景别过渡（如远景→中景）
- **建立→推进→强调**：先用远景/全景建立空间，再用中景推进叙事，最后用近景/特写强调情绪
- **竖屏短剧特殊考量**：9:16画幅下优先使用中景和近景，突出人物上半身和面部表情

#### 180度轴线规则（180-Degree Rule）

- **定义**：在两角色之间建立一条假想的"轴线"，摄像机始终保持在轴线的同一侧拍摄
- **作用**：保持角色之间的左/右空间关系一致，观众不会迷失方向
- **遵守**：角色A看右，角色B看左——维持对话场景的空间秩序
- **越轴（Breaking the Line）**：故意打破轴线，制造混乱/不安/意外的心理感受
- **折中方法**：
  - **中性镜头（Neutral Shot）**：直接在轴线上拍摄，重置空间关系
  - **切出镜头（Cutaway）**：插入无方向性的镜头后切换到新轴线
  - **摄像机移动（Camera Movement）**：让观众看到越轴过程，维持方向感

#### 正反打（Shot / Reverse Shot）

- **定义**：在对话场景中，交替拍摄角色A和角色B的镜头
- **使用规律**：
  - 通常使用过肩镜头（Over-the-Shoulder Shot）过渡
  - 必须遵守180度轴线规则
  - 典型模式：建立镜头（两人同框）→ 角色A视角 → 角色B视角 → 返回建立镜头
- **AI画面应用**：每对正反打镜头需要明确声明摄像机位置和角色视线方向

#### 镜头衔接原则

**Cut on Action（动作接点剪辑）：**
- 在两个镜头之间，让同一动作在两个画面中延续完成
- 例如：角色推门的动作在镜头A开始，在镜头B完成
- 确保动作的方向、速度在两个镜头间保持一致

**Match Cut（匹配剪辑）：**
- 通过画面元素（形状、颜色、运动方向）的相似性连接不同场景
- 常用于转场和叙事跳跃

**动接动 / 静接静原则：**
- 运动镜头接运动镜头，静止镜头接静止镜头
- 剪辑点前后的画面运动状态要保持一致

### 1.2 在AI画面指令中的应用

#### 分镜Sequence的Prompt化

将分镜规则直接嵌入画面指令：

```
[景别]：[近景/中景/远景]，镜头角度：[仰拍/平视/俯拍]，焦距：[35mm/50mm/85mm]
[构图]：角色位于画面[左侧/右侧/中央]，视线方向[向左/向右]
[照明]：[自然光/逆光/霓虹]，光源方向：[左上方/右侧]
[情绪]：[紧张/温暖/悬疑]
[上帧衔接]：继承上一帧的[动作/空间/色调]
```

#### 分镜切换检查清单（AI画面生成前校验）

1. 相邻镜头的景别是否跨越至少一级？
2. 对话场景中角色视线方向是否保持一致（180度规则）？
3. 同场景动作是否在接点处连贯？
4. 色调和光效是否在连续镜头中保持一致？
5. 竖屏9:16构图是否突出核心信息？

### 1.3 引用来源

1. **分镜大师全套培训教程** - 今日头条 — https://www.toutiao.com/article/7617039056993370667/
2. **镜头组接原则** - 知乎 — https://zhuanlan.zhihu.com/p/517551150
3. **电影中的镜头景别基础篇** - 知乎 — https://zhuanlan.zhihu.com/p/1990882089227277573
4. **避坑指南：树立分镜意识** - 百度文库 — https://wenku.baidu.com/view/27740466cf1755270722192e453610661ed95abf.html
5. **分镜设计指南** - 彭子骁/博客园 — https://www.cnblogs.com/VisionGo/p/19831725
6. **Storyboard Shot Types Guide** - Storyliner — https://www.storyliner.online/learn/shot-types
7. **Camera Angles for Storyboard Artists** - StoryboardArt — https://storyboardart.org/storyboard-tutorials/camera-angles-for-storyboard-artists/
8. **影视中的轴线概念与越轴方式** - 知乎 — https://zhuanlan.zhihu.com/p/520712660
9. **180度轴线原则详细介绍** - 知乎 — https://zhuanlan.zhihu.com/p/2021891050881435191
10. **What is the 180 Degree Rule in Film** - StudioBinder — https://www.studiobinder.com/blog/what-is-the-180-degree-rule-film/
11. **Continuity Editing and the 180-Degree Rule** - Fiveable — https://fiveable.me/understanding-film/unit-7/continuity-editing-180-degree-rule/study-guide/Mb1avv1f8DMaewzJ
12. **180-Degree Rule In Filmmaking Explained** - FreelanceVideoCollective — https://www.freelancevideocollective.com/180-degree-rule-in-filmmaking/
13. **匹配剪辑详解** - 知乎 — https://zhuanlan.zhihu.com/p/127109879
14. **动作连戏** - 百度百科 — https://baike.baidu.com/item/動-作-連-戲/4040542
15. **影视剪辑与镜头语言** - 百度文库 — https://wenku.baidu.com/view/7336a2af0342a8956bec0975f46527d3240ca623.html
16. **AI短剧分镜规划教程** - 灵绘AI — https://linghuiai.net/guide/ai-drama/storyboard
17. **AI短剧分镜生成全流程教程** - CSDN — https://wenku.csdn.net/doc/5ay2u9066i
18. **AI漫剧/纯AI短剧分镜头脚本怎么写** - 知乎 — https://zhuanlan.zhihu.com/p/2001035973207798718

---

## Part 2: AI生图人物一致性方案

### 2.1 核心方案总结

#### 为什么AI生图人物会"变脸"？

AI视频/图像生成模型本质上是无状态系统——每次生成都是独立的随机过程。根源包括：
1. **随机种子不同**：每次生成使用不同随机数
2. **描述不够精确**：模糊描述如"年轻女性"可以映射到无数种面貌
3. **场景变化影响**：不同光线、角度下模型对人物的"理解"不同
4. **缺乏记忆机制**：当前AI不具备跨次调用的状态保持能力

#### 方案对比矩阵

| 方案 | 技术门槛 | 一致性强度 | 适用场景 | 核心工具 |
|------|---------|-----------|----------|----------|
| 图生视频（Reference Image） | ⭐ 低 | ⭐⭐⭐⭐⭐ | 新手起步、批量生产 | 可灵/即梦 图生视频 |
| 详细角色描述模板 | ⭐ 低 | ⭐⭐⭐⭐ | 灵活多角度 | Prompt工程 |
| 固定Seed值 | ⭐ 低 | ⭐⭐⭐ | 同场景多镜头 | 各平台API |
| AI换脸后期 | ⭐⭐ 中 | ⭐⭐⭐⭐ | 已有素材统一 | 换脸工具 |
| 角色参考图（即梦/可灵） | ⭐ 低 | ⭐⭐⭐⭐ | 在线平台快速生产 | 即梦AI角色特征 |
| IP-Adapter + ControlNet | ⭐⭐⭐ 高 | ⭐⭐⭐⭐⭐ | 本地高精度控制 | ComfyUI / SD WebUI |
| LoRA模型训练 | ⭐⭐⭐ 高 | ⭐⭐⭐⭐⭐ | 长期IP运营 | Kohya/Dreambooth |

#### 方案一：图生视频（最推荐新手）

**步骤：**
1. 用AI生成角色定妆照（正面、半身、高清、纯色背景）
2. 在可灵/即梦中选择"图生视频"模式
3. 上传定妆照作为参考图
4. 提示词描述动作和场景——角色外貌由参考图决定

**定妆照Prompt模板：**
```
Portrait photo of a [描述]：
[年龄]year old [性别], [脸型], [发型颜色+长度], [妆容],
wearing [服装描述], [表情],
studio lighting, clean background, high resolution,
front-facing, shoulders visible
```

#### 方案二：详细角色描述模板

建立固定角色卡片，所有镜头的提示词都复用相同描述：

```
【角色卡片 - 基础特征】
[姓名], [年龄], [身高], [体型]

【面部】
[脸型], [眼型], [鼻型], [唇型], [肤色]

【发型】
[发型描述], [长度], [颜色]

【标志特征】
[痣/疤痕/眼镜等独特特征]

【服装系统】
- 日常：[具体服装+材质+颜色]
- 居家：[具体服装+材质+颜色]
- 正式：[具体服装+材质+颜色]
```

**使用方法：** 每个镜头的提示词开头粘贴完整角色描述，最后加动作和场景。

#### 方案三：即梦AI角色一致性功能

这是目前最易用的在线平台方案：

**操作流程：**
1. **生成初始角色**：模型选"图片2.0"，尺寸9:16，加入五官和材质特征词
2. **超清修复**：点击"超清"提升画质
3. **上传参考图**：在"角色特征"选项中上传定妆照
4. **设置参考强度**：
   - 默认强度（70-80）：保持面部+发型+服装全部一致（适合同场景）
   - 低强度（30-50）：仅保留面部特征（适合换装/换背景）
5. **新提示词**：写动作场景描述，保留核心风格词，用`--no`排除干扰项

**避坑参数表：**
- 面部不一致 → 提高"角色特征"强度至80+
- 服装/发型变化 → 新提示词保留服装/发型关键词
- 背景干扰人物 → 添加`--no 杂乱背景`
- 光影不一致 → 保留"柔和光影""丝绸质感"等固定词

#### 方案四：ComfyUI角色一致性工作流

**核心组件链：**

| 组件 | 用途 | 关键参数 |
|------|------|----------|
| **ControlNet Canny** | 锁定角色轮廓结构 | 权重0.4，引导0-0.5 |
| **IP-Adapter FaceID Plus v2** | 精确提取和迁移面部特征 | 权重0.7，全程引导 |
| **ADetailer (face_yolov8n)** | 多人物自动面部修复 | 自动检测+修复 |
| **大模型** | ProtoVision XL-High Fidelity 推荐 | SDXL系列 |

**生成多视角角色网格：**
```
Prompt: character sheet, color photo of [角色],
white background, [发型], [特征], [服装]

ControlNet: Canny SDXL (权重0.4) + IP-Adapter FaceID (权重0.7)
底部输出: 同角色的正面/侧面/3/4角度网格图
```

**Consistent Character Creator 3.0（现成工作流）：**
- 基于Qwen Image Edit模型
- 单张参考图→多角度一致角色
- 可在4GB显存消费级GPU上运行

#### 方案五：LoRA模型训练（专业方案）

**适用场景：** 长期运营同一角色IP

**步骤：**
1. 收集10-20张角色的多角度、多表情照片
2. 使用Kohya Trainer或Dreambooth工具训练
3. 导出LoRA文件（体积小，约10-150MB）
4. 生成时加载：`<lora:角色名:0.7-0.9>`
5. 配合ControlNet做姿态和构图控制

### 2.2 在AI画面指令中的应用

#### 一致性Prompt模块化设计

```
[角色锚定模块] — 复用不变
+ 基础特征：Chinese woman, 25yo, 165cm, slim
+ 面部：oval face, double eyelids, small nose
+ 发型：long straight black hair, center-parted, mid-back length
+ 标志：small mole below left eye
+ 本场服装：white silk blouse + black pencil skirt + nude heels

[场景变化模块] — 每镜头更新
+ 位置：cafe interior / street / home
+ 动作：walking / sitting / looking at phone
+ 情绪：happy / worried / determined

[一致性参数]
+ Seed：[固定值]
+ 参考图强度：[70-80]
+ Style锚定词：保持相同风格描述词
```

#### 辅助一致性策略

1. **服装作为锚点**：即使面部有细微差异，相同服装即可让观众认为是同一人
2. **快速剪辑掩盖**：每个镜头2-4秒，观众来不及对比面部细节
3. **避免正面特写连续对比**：不同镜头中若面部差异较大，中间插入环境空镜过渡
4. **统一后期调色**：不同镜头的色调差异会放大不一致感
5. **多角度分镜提示词公式**：`同一角色，多角度，连贯动作`

### 2.3 引用来源

1. **AI短剧角色一致性全解析** - 550W AI — https://www.550wai.cn/blog/ai-short-drama-character-consistency.html
2. **AI绘画角色一致性怎么做** - Cursor-IDE — https://www.cursor-ide.com/blog/ai-drawing-character-consistency-guide-2025
3. **Stable Diffusion角色一致性** - 技术栈 — https://jishuzhan.net/article/1876838766111363074
4. **如何保证每次都画出同一张人脸** - 知乎 — https://zhuanlan.zhihu.com/p/636670339
5. **即梦+可灵实现人物一致性** - 知乎 — https://zhuanlan.zhihu.com/p/1887821957254329621
6. **即梦AI角色一致性教程** - 今日头条 — https://www.toutiao.com/article/7482307049473278518/
7. **ComfyUI角色一致性完整方案** - 知乎 — https://zhuanlan.zhihu.com/p/1943151979590292076
8. **Consistent Character Creator 3.0** - RunComfy — https://www.runcomfy.com/zh-CN/comfyui-workflows/consistent-character-creator-3-0
9. **ComfyUI角色一致性工作流** - CharacterLock — https://characterlock.ai/blog/comfyui-consistent-character
10. **IP-Adapter项目官网** — https://ip-adapter.github.io/
11. **DarkWaterReflection角色一致性ComfyUI** - GitHub — https://github.com/DarkWaterReflection/character-consistency-comfyui
12. **ComfyUI+ControlNet+IP-Adapter精准控图** - Circler — https://circler.cn/article_info/504/
13. **AI绘画多图角色一致性终极秘诀** - PHP中文网 — https://www.php.cn/faq/1534679.html
14. **AI短剧角色一致性技术全解析** - 搜狐 — https://www.sohu.com/a/1003938540_122690230
15. **AI漫剧角色一致性LoRA+IPAdapter全攻略** - 2DS — https://www.2ds.cn/ai漫剧角色一致性全攻略：lora训练与ipadapter实战/
16. **一人一剧组！多人物一致性教程** - 今日头条 — https://www.toutiao.com/article/7623367801603883554/

---

## Part 3: awesome-gpt-image-2 模板细节

### 3.1 项目概览

- **仓库地址**：https://github.com/freestylefly/awesome-gpt-image-2
- **模板文档**：https://github.com/freestylefly/awesome-gpt-image-2/blob/main/docs/templates.md
- **案例总数**：508个完整案例
- **模板分类**：20+套工业级模板，按4个类别组织

### 3.2 Photography & Realism 分类模板

#### 常规模板

```
拍摄主题：[人物/物品/街景]，场景为[地点]。
摄影参数风格：[35mm/85mm]，[浅景深/深景深]，[纪实/电影感]。
光线：[自然光/夜景霓虹/逆光]，情绪：[情绪词]。
细节要求：[肤质/材质/颗粒感]。
输出：高写实摄影风格图像。
```

**Schema 字段定义：**

| 字段 | 类型 | 说明 | 示例值 |
|------|------|------|--------|
| `subject` | String | 拍摄主体类型 | 人物 / 物品 / 街景 |
| `scene` | String | 拍摄场景地点 | 具体地点描述 |
| `camera_style` | Enum[] | 摄影参数风格 | 35mm / 85mm |
| `depth_of_field` | Enum | 景深类型 | 浅景深 / 深景深 |
| `aesthetic` | Enum | 视觉风格 | 纪实 / 电影感 |
| `lighting` | String | 光线类型 | 自然光 / 夜景霓虹 / 逆光 |
| `mood` | String | 情绪关键词 | 情绪词 |
| `details` | String | 细节要求 | 肤质 / 材质 / 颗粒感 |
| `output` | Const | 输出类型 | 高写实摄影风格图像 |

**组合规则：**
- `subject` + `scene` → 基础场景
- `camera_style` + `depth_of_field` + `aesthetic` → 摄影语言
- `lighting` + `mood` → 画面情绪
- `details` → 真实感增强

#### JSON进阶模板

```json
{
  "type": "Hyper-realistic Photography",
  "subject": {
    "description": "A weary 30-year-old barista wiping a coffee cup",
    "details": "Subtle sweat on forehead, detailed skin pores, wearing a denim apron"
  },
  "setting": "Dimly lit vintage cafe, rain visible through the window behind",
  "camera_specs": {
    "gear": "Shot on Sony A7R IV, 50mm lens",
    "aperture": "f/1.4 (shallow depth of field, background completely blurred)",
    "lighting": "Cinematic lighting, neon sign reflecting on wet window, soft rim light on subject's hair"
  },
  "film_aesthetic": "Kodak Portra 400 emulation, subtle film grain"
}
```

**JSON Schema层级定义：**

| 字段路径 | 类型 | 说明 |
|----------|------|------|
| `type` | Const | `"Hyper-realistic Photography"` |
| `subject.description` | String | 主体详细描述（年龄、职业、动作） |
| `subject.details` | String | 微观细节（汗水、毛孔、服装材质） |
| `setting` | String | 环境场景 |
| `camera_specs.gear` | String | 相机型号+镜头 |
| `camera_specs.aperture` | String | 光圈参数+效果说明 |
| `camera_specs.lighting` | String | 布光方案 |
| `film_aesthetic` | String | 胶片模拟（如Kodak Portra 400） |

#### 街头纪实摄影模板

```
生成一张竖版手机纪实照片，主题是[意外事件/日常瞬间]发生在[街头/室外地点]。
主体：[物品/人物动作/现场痕迹]，必须呈现真实的材质状态，
例如[液体扩散/冰块散落/纸张褶皱/灰尘颗粒]。
环境：[地面材质/墙面/街景元素]，保留自然杂乱和生活痕迹。
光线：[正午强光/阴天散射光/夜间路灯]，阴影要符合真实方向，
可加入[人物影子/路牌影子/树影]。
镜头：手持手机视角，略微俯拍或低角度，构图自然，像随手拍到的现场。
画面质感：raw unedited photo look，自然色彩，真实纹理，高细节。
负面约束：不要插画、动漫、CGI、棚拍光、过度干净、过度构图、
假液体、漂浮物、品牌文字、水印、海报设计感。
输出：一张可信的日常纪实摄影图。
```

**摄影类避坑要点：**
- **加点瑕疵**：皮肤纹理（skin pores）、雀斑、胶片颗粒（film grain）→ 真实感拉满
- **用参数说话**：`f/1.4` 代替"浅景深"，`50mm` 代替"半身照"
- **写具体不完美**：写"粗糙石砖、散落冰块、自然阴影、轻微手持感"

### 3.3 Scenes & Storytelling 分类模板

#### 常规模板

```
生成[故事主题]场景图，发生在[时间+地点]。
主事件：[事件描述]，主角：[角色]，冲突点：[冲突]。
镜头语言：[广角建立镜头/中景叙事/特写]。
氛围：[紧张/温暖/悬疑]，色调：[冷/暖/高反差]。
输出：具备叙事张力的场景概念图。
```

**Schema 字段定义：**

| 字段 | 类型 | 说明 |
|------|------|------|
| `story_theme` | String | 故事主题 |
| `time_place` | String | 时间+地点 |
| `main_event` | String | 主事件描述 |
| `protagonist` | String | 主角 |
| `conflict` | String | 冲突点 |
| `camera_language` | Enum | 镜头语言（广角建立/中景叙事/特写） |
| `atmosphere` | Enum | 氛围（紧张/温暖/悬疑） |
| `color_tone` | Enum | 色调（冷/暖/高反差） |
| `output` | Const | 叙事张力场景概念图 |

**组合规则：**
- `story_theme` + `time_place` → 叙事坐标
- `main_event` + `protagonist` + `conflict` → 戏剧三角
- `camera_language` → 视觉叙事节奏
- `atmosphere` + `color_tone` → 情绪调性统一

#### JSON进阶模板

```json
{
  "type": "Narrative Scene",
  "story_context": "The exact moment an ancient seal breaks",
  "environment": "Crumbling stone temple overgrown with glowing blue vines",
  "action": "A young explorer dropping their torch as a massive beam of light shoots into the sky",
  "atmosphere": {
    "mood": "Awe-inspiring, terrifying",
    "lighting": "Blinding central light casting long dramatic shadows"
  },
  "camera": "Low angle shot, emphasizing the scale of the light beam"
}
```

**场景类避坑要点：**
- **要有"动词"**：叙事图必须写"事件"（如"正在崩塌"、"刚点燃火把"），让画面动起来
- **用镜头语言**：使用"Low angle shot（低角度仰拍）"或"Dutch angle（倾斜镜头）"增加戏剧冲突

### 3.4 两分类核心差异对比

| 维度 | 摄影与写实 | 场景与叙事 |
|------|-----------|-----------|
| **核心目标** | 高度写实的摄影质感 | 具备叙事张力的概念图 |
| **关键字段** | 相机参数（gear/aperture/film）、材质细节 | 事件（action）、冲突（conflict）、镜头语言（camera） |
| **真实感来源** | 物理瑕疵（毛孔/颗粒/不完美） | 戏剧性瞬间（动词/事件/光影冲突） |
| **控制手段** | 摄影参数精确量化 | 镜头角度+情绪氛围联动 |
| **JSON type 标识** | `Hyper-realistic Photography` | `Narrative Scene` |

### 3.5 原子化Schema组合规则总结

awesome-gpt-image-2的模板设计遵循**分层组合**原则：

```
第一层：类型锚定 (type)
    → 决定整体输出方向和约束集

第二层：主体描述 (subject/action/story_context)
    → 定义画面的核心叙事内容

第三层：环境参数 (setting/environment)
    → 提供空间和时间上下文

第四层：技术参数 (camera_specs/camera/lighting)
    → 精确控制视觉呈现手段

第五层：质感后处理 (film_aesthetic/details/atmosphere.mood)
    → 统一风格和情绪调性

第六层：负面约束 (negative_constraints)
    → 排除不希望出现的元素
```

**对AI画面指令Skill的启示：**
- 将分镜指令模块化为可组合的Schema字段
- 每个镜头 = `[景别] + [摄影参数] + [角色锚定] + [场景变化] + [情绪氛围] + [约束排除]`
- 模板继承：同一场景的连续镜头共享基础参数，仅更新变化字段

### 3.6 引用来源

1. **awesome-gpt-image-2 仓库主页** — https://github.com/freestylefly/awesome-gpt-image-2
2. **templates.md 模板文档** — https://github.com/freestylefly/awesome-gpt-image-2/blob/main/docs/templates.md
3. **gallery.md 案例画廊** — https://github.com/freestylefly/awesome-gpt-image-2/blob/main/docs/gallery.md
4. **Photography & Realism 模板锚点** — https://github.com/freestylefly/awesome-gpt-image-2/blob/main/docs/templates.md#tpl-photo
5. **Scenes & Storytelling 模板锚点** — https://github.com/freestylefly/awesome-gpt-image-2/blob/main/docs/templates.md#tpl-scene
6. **案例508: Komorebi Garden Overhead Portrait** — https://github.com/freestylefly/awesome-gpt-image-2/blob/main/docs/gallery-part-2.md
7. **案例339: Apple-Style Nature Science Poster** — https://github.com/freestylefly/awesome-gpt-image-2/blob/main/docs/gallery-part-2.md
8. **案例330: Moonlit Livestream Scene** — https://github.com/freestylefly/awesome-gpt-image-2/blob/main/docs/gallery-part-2.md

---

## 附录：跨主题整合——AI短剧画面指令的完整信息架构

基于三个主题的调研，AI短剧画面指令Skill应整合以下模块：

```
┌─────────────────────────────────────────────────────┐
│            AI短剧画面指令生成器                         │
├─────────────────┬───────────────────────────────────┤
│  Part 1: 分镜语法  │  控制画面"怎么拍"                   │
│  - 景别序列选择    │  远景/全景→中景→近景/特写              │
│  - 180度轴线规则   │  角色视线方向一致性                   │
│  - 镜头衔接模式    │  Cut on Action / Match Cut         │
│  - 竖屏构图适配    │  9:16画幅特殊约束                    │
├─────────────────┼───────────────────────────────────┤
│  Part 2: 角色一致性 │  控制画面"谁在画面里"                 │
│  - 角色卡片模板    │  面部+发型+服装+标志特征                │
│  - 参考图注入      │  即梦/可灵角色特征强度                 │
│  - Seed管理       │  同角色同Seed                        │
│  - 换装/场景适配   │  固定服装描述、排除干扰词                │
├─────────────────┼───────────────────────────────────┤
│  Part 3: 模板Schema │  控制画面"长什么样"                  │
│  - 摄影参数模板    │  f/x.x, 35mm, Kodak Portra emulsion  │
│  - 叙事场景模板    │  Action+Conflict+Atmosphere          │
│  - 层级化组合      │  Type→Subject→Setting→Params→Quality  │
│  - 负面约束清单    │  排除非目标风格元素                     │
└─────────────────┴───────────────────────────────────┘
```

**一镜的完整生成指令结构：**

```
[镜头号: 03 | 景别: 中景 | 时长: 4s]
[摄影: 50mm, f/2.8, 电影感, 暖色调]
[角色: 女主卡片A, 日常服装套, 视线方向: 右]
[场景: 咖啡店内, 下午3点, 窗边座位]
[动作: 端起咖啡杯, 看向窗外]
[情感: 若有所思, 温暖柔和]
[衔接: 接镜02推门动作, 动接动, 动作速度匹配]
[约束: --no 现代元素, 真人写实风格, 胶片颗粒]
[Seed: 固定12345, 参考图强度: 75]
```
