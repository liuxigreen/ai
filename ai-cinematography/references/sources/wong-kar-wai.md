# 王家卫（Wong Kar-wai）电影视觉语法体系

> **用途说明**：本文档提取王家卫电影的可量化视觉规则，用于 AI 画面指令（Midjourney / Stable Diffusion / ComfyUI / 视频生成模型）的 Prompt 编写。
>
> **方法论**：每个视觉特征均标注 **"Prompt 化"** 字段，给出可直接使用的英文/中文关键词。
>
> **搜索来源**：共 10 个来源，均已在对应位置标注 URL。

---

## 1. 色彩体系

### 1.1 四大色系总览

| 色系 | 代表影片 | 情绪指向 | HEX 参考范围 |
|------|----------|----------|-------------|
| **红色系** | 《花样年华》《旺角卡门》 | 欲望、激情、危险、压抑 | `#8B0000` ~ `#DC143C` |
| **绿色系** | 《阿飞正传》《重庆森林》《花样年华》 | 怀旧、压抑的生命力、出轨/嫉妒 | `#2E8B57` ~ `#556B2F` |
| **黄色/暖金系** | 《东邪西毒》《一代宗师》《花样年华》 | 沧桑、暧昧、时代乡愁 | `#DAA520` ~ `#B8860B` |
| **蓝紫色系** | 《重庆森林》《春光乍泄》《旺角卡门》 | 忧郁、孤独、冷漠、疏离 | `#191970` ~ `#4B0082` |

> 来源：[豆瓣 - 王家卫最全电影配色赏析](https://www.douban.com/note/787539660/)、[知乎 - 电影摄影中的色彩应用研究](https://zhuanlan.zhihu.com/p/15855539582)

---

### 1.2 分影片配色详解

#### 《重庆森林》（1994）

| 角色/场景 | 主色调 | 象征意义 |
|-----------|--------|----------|
| 金城武（失恋警察） | **绿色** | 困顿、迷茫（凤梨罐头场景、金鱼缸光线） |
| 林青霞（神秘女子） | **黄色** | 欲望与放纵边缘（黄色假发、雨衣） |
| 王菲（快餐店女孩） | **黄色**（明亮版） | 白日梦式纯真、活力 |
| 梁朝伟（警察663） | **蓝色** | 忧郁失恋、制服蓝、蓝紫色房间 |
| 城市背景 | 霓虹多彩 | 黄色M记、Coca-Cola红、Circle K——城市变幻莫测 |

> **Prompt 化**：
> - 中文：高饱和度的绿色调光、金鱼缸透出的霓虹绿、蓝紫色忧郁房间、明黄色服饰
> - 英文：`emerald green aquarium light, neon green interior, blue-purple melancholy room, bright yellow raincoat and wig`

---

#### 《花样年华》（2000）

| 场景/元素 | 主色调 | 象征意义 |
|-----------|--------|----------|
| 苏丽珍旗袍 | **红色** 为主（23套旗袍） | 欲望燃烧、情感涌动的视觉外化 |
| 背景基调 | **黑色/褐色/深灰** | 高级感底色，衬托鲜艳旗袍 |
| 绿色旗袍（得知丈夫出轨） | **绿色** | 婚外情的"绿帽子"隐喻 |
| 整体滤镜 | **暖黄/金色** | 旧照片般的怀旧感、"花样年华"的时代追忆 |
| 周慕云西装 | **灰色** | 矛盾、不自信、逃避 |

> **Prompt 化**：
> - 中文：暖金色怀旧滤镜、深红丝绸旗袍在暗色背景下、低色温琥珀光、绿色旗袍的点晴之笔
> - 英文：`warm amber nostalgic filter, deep red silk cheongsam against dark background, low color temperature tungsten light, rich saturated red with black negative space`

> 来源：[色彩文化 - In the Mood for Love 摄影分析](https://colorculture.org/cinematography-analysis-of-in-the-mood-for-love/)、[知乎 - 符号学拆解花样年华](https://zhuanlan.zhihu.com/p/2026306286665352773)

---

#### 《春光乍泄》（1997）

| 场景 | 色调特征 |
|------|----------|
| 开头分离 | **黑白** → 传递孤独 |
| 复合后 | **彩色**（红/黄/暖） → 黎耀辉衣服从灰变红 |
| 矛盾后 | **蓝色**（冷调） → 绝望笼罩湖水与街道 |
| 布宜诺斯艾利斯 | **绿色调** → 南美异域风情 |
| 酒吧 | **红色** → 夜晚气质 |

> **Prompt 化**：
> - 中文：黑白渐变彩色、布宜诺斯艾利斯的绿色异域调、红色酒吧内景、冷蓝绝望色调
> - 英文：`black and white to color transition, Buenos Aires green-tinted exoticism, deep red bar interior, cold blue desaturated despair`

---

#### 《2046》（2004）

- 整体：**暗色调** + 灯红酒绿下的鲜明色彩
- 强对比配色：暗色街角 + 斑驳深色 + 艳丽服装
- 视觉感受：**克制的艳丽** → 压抑感

> **Prompt 化**：
> - 中文：暗色调底色上的高饱和点缀色、灯红酒绿但克制、暗角深色街墙斑驳
> - 英文：`dark base with highly saturated accent colors, neon nightlife with restrained palette, moody dark corners with vivid costume colors`

---

#### 《堕落天使》（1995）

- 霓虹灯光谱：**青蓝/品红/暖黄** 三色主导
- 广角畸变镜头下的霓虹反射
- "smudge-motion" 让霓虹在画面上形成拖影

> **Prompt 化**：
> - 中文：青蓝色霓虹光溢出、品红色招牌反射、暖黄街灯光晕 + 运动拖影
> - 英文：`teal neon spill, magenta sign reflection, warm sodium streetlight glow with motion smear`

> 来源：[HASTA - Neon Romanticism: Fallen Angels](http://www.hasta-standrews.com/features/2025/9/25/neon-romanticism-wong-kar-wais-fallen-angels-and-the-afterlife-of-nineteenth-century-longing)

---

### 1.3 色温使用规律

| 情绪/场景 | 色温 | 色调 | 代表影片案例 |
|-----------|------|------|-------------|
| **孤独、疏离** | 高色温（冷调） | 蓝/青/紫 | 重庆森林警察663、春光乍泄分离期 |
| **浪漫、暧昧** | 低色温（暖调） | 琥珀/金黄/红 | 花样年华全片、重庆森林金城武&林青霞 |
| **怀旧、时间流逝** | 低色温 + 黄色滤镜 | 昏黄/棕褐 | 东邪西毒沙漠、花样年华整体滤镜 |
| **焦虑、危险** | 冷暖交替/高对比 | 红vs蓝、绿vs紫 | 旺角卡门、堕落天使 |

> **Prompt 化**：
> - 冷调疏离：`cool color temperature, blue-tinted shadows, tungsten white balance for cold mood`
> - 暖调浪漫：`warm amber color temperature, golden hour filter, low kelvin tungsten glow`
> - 怀旧：`sepia-toned warmth, faded vintage color, yellowed film stock look`

> 来源：[ReelMind - Wong Kar-wai Cinematography Style](https://reelmind.ai/blog/wong-kar-wai-cinematography-style-training-a-custom-model-for-neo-noir-aesthetics)、[知乎 - 电影摄影色彩研究](https://zhuanlan.zhihu.com/p/15855539582)

---

## 2. 构图偏好

### 2.1 六大核心构图法则

| 构图技法 | 具体形态 | 功能 | 代表影片 |
|----------|----------|------|----------|
| **框架式构图** | 人物置于门框/窗框/走廊线条内 | 暗示道德枷锁、社会规范束缚 | 花样年华、2046 |
| **前景遮挡** | 窗帘/衣柜/墙角/模糊背影遮挡 | 制造窥视感、暗示关系隐秘 | 花样年华、重庆森林 |
| **人物偏置** | 人物放在画面边缘，大量留白（负空间） | 强化孤立感、孤独 | 花样年华、阿飞正传 |
| **镜面反射** | 镜子/玻璃/湿路面/水洼中反射人物 | 情感隔离、多层现实 | 堕落天使、重庆森林 |
| **广角畸变** | 超广角镜头下的面部特写 | 制造疏离感、城市压迫 | 堕落天使 |
| **纵深空间** | 人物在中/后景，前景有遮挡物 | 打破平面结构、舞台化"失真" | 东邪西毒、一代宗师 |

> 来源：[百度百科 - 王家卫风](https://baike.baidu.com/item/%E7%8E%8B%E5%AE%B6%E5%8D%AB%E9%A3%8E/65710983)、[知乎 - 符号学拆解花样年华](https://zhuanlan.zhihu.com/p/2026306286665352773)

---

### 2.2 构图 → Prompt 描述

| 构图技法 | AI Prompt 英文 | AI Prompt 中文 |
|----------|--------------|--------------|
| 框架式构图 | `frame within a frame, subject seen through doorway, window frame composition, trapped by geometric lines` | 框中框构图、透过门框拍摄主体、被几何线条困住 |
| 前景遮挡 | `foreground obstruction, shot through curtains, partial view behind furniture, voyeuristic perspective` | 前景遮挡、透过窗帘拍摄、半掩视角、窥视感 |
| 人物偏置 | `off-center composition, negative space, isolated figure in corner, subject placed at rule of thirds extreme` | 偏置构图、大量留白、人物置于角落、极端三分法 |
| 镜面反射 | `mirror reflection, wet pavement reflection, glass partition, double reflection in window` | 镜中反射、湿路面倒影、玻璃隔断、双层反射 |
| 广角畸变 | `wide angle lens distortion, close-up with fisheye, exaggerated facial features, claustrophobic wide shot` | 广角畸变、鱼眼特写、面部夸大、幽闭广角 |
| 纵深空间 | `deep space composition, subject in middle ground, foreground shadow element, layered depth` | 纵深空间、主体在中景、前景阴影元素、层次深度 |

> 来源：[ReelMind - AI training visual tags](https://reelmind.ai/blog/wong-kar-wai-cinematography-style-training-a-custom-model-for-neo-noir-aesthetics)

---

### 2.3 抽帧/慢镜/升格的节奏规律

王家卫著名的 "Step-Printing"（偷格加印）技术原理：

```
拍摄帧率： 6fps（降格拍摄）
↓
每帧复制 4 次（Step-Printing）
↓
放入 24fps 时间线 → 获得 "正常速度"
↓
结果：画面有拖影 + 频闪（strobeing + smearing）
```

| 参数组合 | 效果 | 用途 |
|----------|------|------|
| 12fps + 180° 快门 → 50% 慢放 | 轻度拖影 | 轻微迷失感 |
| **6fps + 180° 快门 → 25% 慢放** | **经典王家卫拖影** | 孤独漂泊、鱼离开水 |
| 3fps + 360° 快门 → 12.5% 慢放 | 极度拖影 + 频闪 | 时间悬置、强烈情感 |
| 标准升格（overcranking） | 流畅慢动作 | 浪漫瞬间延长 |

> **Prompt 化**：
> - 中文：运动拖影效果、抽帧频闪、慢门拍摄、时间悬置感、人物如幽灵般留下残影
> - 英文：`step-printing effect, motion smear, strobing slow motion, undercranked footage aesthetic, ghost-like motion trail, temporal suspension`

> 来源：[Austin Schmidt - Step-Printing Test](https://www.austinschmidt.com/blog-/step-printing-wong-kar-wai)

---

## 3. 光影特征

### 3.1 光源体系

| 光源类型 | 效果 | 代表场景 |
|----------|------|----------|
| **霓虹灯** | 单色高饱和面光源、青蓝/品红/暖黄三色为主 | 堕落天使、重庆森林 |
| **街灯/钠灯** | 暖黄钨丝光、低色温 | 花样年华楼梯间 |
| **台灯/实用光源** | 局部照亮、大面积阴影 | 花样年华室内、2046 |
| **电视/荧光灯** | 闪烁冷光、日光灯焦虑 | 重庆森林 |
| **点光源硬光** | 面部半明半暗、伦勃朗光 | 花样年华、东邪西毒 |

> **Prompt 化**：
> - 中文：霓虹灯光为主要光源、钠灯暖黄街灯、台灯局部照明+深邃阴影、硬质点光源面部半阴影
> - 英文：`practical lighting motivated source, neon spill as key light, sodium streetlamp warm glow, hard point source with Rembrandt lighting, half face in shadow`

---

### 3.2 布光策略

| 策略 | 技术描述 | 情绪功能 |
|------|----------|----------|
| **低调布光** | 大面积阴影、高光比（neo-noir） | 道德模糊、隐秘、见不得光 |
| **硬光面部阴影** | 点光源直打、半边脸隐没 | 情绪内敛、不可读 |
| **体积光效** | 烟雾中的光柱、Rayleigh散射 | 氛围密度、视觉诗意 |
| **逆光与剪影** | 背光轮廓、人物剪影 | 戏剧性、神秘感 |
| **伦勃朗光** | 三角光位、颧骨下方三角形高光 | 经典造型、内心复杂 |
| **栅栏投影** | 透过百叶窗/栅栏的光影网 | 牢笼隐喻、困住的情感 |

> **Prompt 化**：
> - 中文：新黑色电影低调布光、体积光效+烟雾粒子、逆光剪影轮廓、百叶窗栅栏光影投射面部
> - 英文：`neo-noir low-key lighting, volumetric light shafts through smoke, backlit silhouette, Venetian blind shadow pattern on face, chiaroscuro high contrast`

---

### 3.3 氛围元素

| 元素 | 视觉作用 | Prompt 描述 |
|------|----------|-------------|
| **烟雾** | 体积光载体、氛围密度 | `cigarette smoke curling in light, atmospheric haze, smoke-filled room` |
| **雨** | 湿路面反射、霓虹倒影拉长 | `rain-slicked streets, wet pavement reflection, neon reflecting in puddles` |
| **镜面/玻璃** | 多层反射、窥视视角 | `smudged mirror reflection, condensation on glass, character seen through wet window` |
| **胶片颗粒** | 质感、年代感 | `film grain texture, gritty analog quality, scratched film stock` |
| **运动模糊** | 情感强度、时间流逝 | `motion blur, dragged shutter, ghostly afterimage` |

> 来源：[ShutterGroove - Fujifilm Recipes Guide](https://www.shuttergroove.com/reviews/photography/wong-kar-wai-fujifilm-recipes-guide/)、[ReelMind - AI training visual tags](https://reelmind.ai/blog/wong-kar-wai-cinematography-style-training-a-custom-model-for-neo-noir-aesthetics)

---

## 4. 镜头语言 → Prompt 化

### 4.1 景别偏好

| 景别 | 使用频率 | 功能 | Prompt 化 |
|------|----------|------|-----------|
| **大特写** | 极高 | 怼脸拍、情感聚焦、面部表情极致 | `extreme close-up on face, intimate facial detail` |
| **中近景** | 高 | 人物关系、对话、身体距离 | `medium close-up, two-shot with tension` |
| **广角全景** | 中 | 城市孤独、空间压迫 | `wide angle establishing shot, claustrophobic interior` |
| **空镜** | 中 | 时间流逝、氛围转换 | `empty city shot, time-lapse urban landscape` |

---

### 4.2 机位习惯

| 机位 | 使用场景 | Prompt 化 |
|------|----------|-----------|
| **手持摄影** | 都市游荡、情绪躁动 | `handheld camera, shaky urban following shot, restless camera movement` |
| **低角度** | 城市蔓延感、反射面 | `low angle, looking up through neon, urban sprawl perspective` |
| **固定机位 + 慢摇** | 静观、窥视 | `static camera with subtle pan, locked-off composition, voyeuristic stillness` |
| **跟拍** | 人物穿行街道/楼道 | `tracking shot following subject, smooth dolly through narrow corridor` |
| **单机位** | 精细控制构图与光线 | `single camera setup, controlled composition` |

---

### 4.3 镜头参数特征

| 参数 | 王家卫偏好 | Prompt 化 |
|------|-----------|-----------|
| **焦段** | 广角（超广角畸变）+ 长焦（空间压缩） | `wide angle distortion on face, telephoto compression in narrow space` |
| **景深** | 浅景深（模糊背景）、移焦 | `shallow depth of field, rack focus, blurred bokeh background` |
| **快门** | 慢门（运动拖影）、6fps降格 | `slow shutter drag, undercranked motion blur, 6fps aesthetic` |
| **画幅** | 1.85:1 或 2.35:1 宽银幕 | `widescreen cinematic ratio, anamorphic aspect ratio` |
| **胶片感** | 颗粒、色差、镜头畸变 | `film grain, chromatic aberration, lens imperfection, analog film look` |

> 来源：[百度百科 - 王家卫风](https://baike.baidu.com/item/%E7%8E%8B%E5%AE%B6%E5%8D%AB%E9%A3%8E/65710983)、[色彩文化 - Cinematography Analysis](https://colorculture.org/cinematography-analysis-of-in-the-mood-for-love/)

---

### 4.4 完整 Prompt 模板

#### 模板 A：英文（通用 AI 生图）

```
[Subject description], Wong Kar-wai cinematic style, highly saturated emotional 
color grading (deep red #8B0000, emerald green #2E8B57, electric blue #191970), 
slow shutter motion blur, step-printing effect, handheld camera aesthetic, 
frame within a frame composition, foreground obstruction through curtains,
neo-noir low-key lighting, practical neon light source, cigarette smoke 
atmosphere, rain-slicked street with neon reflections, shallow depth of field 
with dreamy bokeh, film grain texture, urban isolation mood, 
romantic melancholy, In the Mood for Love inspired, In the Mood for Love inspired
```

#### 模板 B：中文（国产大模型）

```
[主体描述]，王家卫电影风格，高饱和度情绪化色彩（深红/翡翠绿/电蓝），
慢门运动拖影，抽帧效果，手持摄影美学，框中框构图，前景遮挡（透过窗帘），
新黑色电影低调布光，霓虹灯实用光源，香烟烟雾缭绕，雨湿街道霓虹倒影，
浅景深梦幻焦外，胶片颗粒质感，都市疏离氛围，浪漫忧郁情绪，花样年华风格
```

> 来源：[优设 - AI电影美学提示词](https://www.uisdc.com/ai-cinema-prompts)

---

## 5. 情绪 → 画面指令映射表

### 5.1 主情绪映射

| 情绪 | 色调方案 | 构图法则 | 光影特征 | 画面元素 | AI Prompt 关键词 |
|------|----------|----------|----------|----------|-----------------|
| **孤独 / 疏离** | 蓝紫色系 + 绿色系（冷调高色温） | 人物偏置 + 大量负空间 + 广角畸变 | 低调布光、面部半阴影、单一实用光源 | 空旷街道、电话亭、便利商店、鱼缸 | `blue-purple cold palette, off-center isolated figure, wide angle distortion, low-key lighting, lone figure in empty city, melancholic solitude` |
| **浪漫 / 暧昧** | 红色系 + 暖金色（低色温） | 框架式构图 + 前景遮挡 + 慢镜头 | 暖黄钨丝光、台灯光源、伦勃朗光 | 旗袍、狭窄楼梯、雨夜、华尔兹 | `deep red and warm amber, frame within a frame, slow motion, tungsten romantic glow, intimate staircase encounter, unspoken desire` |
| **怀旧 / 时间流逝** | 黄色系 + 棕褐色（低色温复古滤镜） | 镜面反射 + 纵深空间 + 抽帧 | 体积光效 + 烟雾 + 胶片颗粒 | 旧时钟、泛黄照片、老式收音机、吴哥窟 | `sepia-warm vintage filter, mirror reflection, step-printing motion smear, film grain, faded memory aesthetic, passage of time` |
| **欲望 / 压抑** | 红色 vs 绿色对比（高饱和） | 狭窄空间 + 栅栏投影 + 二次框定 | 硬光面部半阴影、霓虹光溢出 | 红色窗帘、绿色墙壁、百叶窗光影 | `red vs green high contrast, claustrophobic framing, venetian blind shadow, hard light half face, forbidden desire, moral confinement` |
| **焦虑 / 危险** | 红蓝交替（冷暖高对比） | 手持晃动 + 广角畸变 + 快速跟拍 | 闪烁荧光灯、霓虹闪烁 | 雨夜街道、摩托飞驰、人群中的孤独 | `red-blue alternating palette, shaky handheld, flickering fluorescent, motion blur urgency, urban anxiety, neon flicker` |
| **都市漂泊** | 霓虹多色 + 深黑底色 | 跟拍 + 低角度 + 镜面反射 | 湿路面反射、霓虹光晕、实用光源 | 香港街道、霓虹招牌、重庆大厦、深夜便利店 | `neon multicolor on black, tracking shot low angle, wet pavement reflection, Hong Kong street night, urban nomad, 24-hour convenience store` |

---

### 5.2 情绪组合标签（Emotion-Visual Compound Tags）

来自 ReelMind AI 训练标签体系：

```
"Isolation Post-Midnight"          →  午夜后的孤独 →  蓝紫+空镜+偏向一边的构图
"Flickering Fluorescent Anxiety"   →  日光灯焦虑  →  冷白闪烁+手持晃动+浅景深
"Longing Gaze Through Glass"       →  透过玻璃渴望 →  镜面反射+前景遮挡+中近景
"Lived-in Melancholy"              →  生活化忧郁 →  绿色调+台灯+胶片颗粒
"Existential Malaise"              →  存在主义不安 →  广角畸变+负空间+低布光
"Unrequited Desire"                →  无回报渴望 →  红色+栅栏光影+框架构图
"Temporal Dislocation"             →  时间错位   →  抽帧拖影+慢镜头+延时
```

> 来源：[ReelMind - AI training narrative metadata](https://reelmind.ai/blog/wong-kar-wai-cinematography-style-training-a-custom-model-for-neo-noir-aesthetics)

---

## 6. 技术参数速查表（Fujifilm 配方参考）

| 参数 | 推荐设置 | 风格效果 |
|------|----------|----------|
| 白平衡 | 钨丝灯（Tungsten）/ 3200K | 暖色低色温光源 |
| ISO | 较高（800-3200） | 增强颗粒感 |
| 快门 | 1/15s 或更慢 | 运动模糊 |
| 颗粒效果 | 强（Strong Grain） | 胶片年代感 |
| 清晰度 | -2 至 -4 | 柔化画面 |
| 镜头 | 23mm / 35mm 大光圈定焦 | 街头感 + 浅景深 |
| 色彩偏移 | R+2, B-2（青色阴影） | Teal & Orange 经典电影对比 |

> 来源：[ShutterGroove - Wong Kar Wai Fujifilm Recipes](https://www.shuttergroove.com/reviews/photography/wong-kar-wai-fujifilm-recipes-guide/)

---

## 7. 来源清单

| # | 标题 | URL |
|---|------|-----|
| 1 | 豆瓣 - 王家卫最全电影配色赏析 | https://www.douban.com/note/787539660/ |
| 2 | 知乎 - 电影摄影中的色彩应用研究 | https://zhuanlan.zhihu.com/p/15855539582 |
| 3 | ReelMind - Training AI for Wong Kar-wai Cinematography | https://reelmind.ai/blog/wong-kar-wai-cinematography-style-training-a-custom-model-for-neo-noir-aesthetics |
| 4 | 优设 - AI电影美学提示词模板 | https://www.uisdc.com/ai-cinema-prompts |
| 5 | 知乎 - 符号学拆解《花样年华》 | https://zhuanlan.zhihu.com/p/2026306286665352773 |
| 6 | Color Culture - In the Mood for Love Cinematography Analysis | https://colorculture.org/cinematography-analysis-of-in-the-mood-for-love/ |
| 7 | Austin Schmidt - Step-Printing Technical Test | https://www.austinschmidt.com/blog-/step-printing-wong-kar-wai |
| 8 | 百度百科 - 王家卫风 | https://baike.baidu.com/item/%E7%8E%8B%E5%AE%B6%E5%8D%AB%E9%A3%8E/65710983 |
| 9 | ShutterGroove - Wong Kar Wai Fujifilm Recipes | https://www.shuttergroove.com/reviews/photography/wong-kar-wai-fujifilm-recipes-guide/ |
| 10 | HASTA - Neon Romanticism: Fallen Angels | http://www.hasta-standrews.com/features/2025/9/25/neon-romanticism-wong-kar-wais-fallen-angels-and-the-afterlife-of-nineteenth-century-longing |

---

## 附录：快速 Prompt 速记卡

### 王家卫风格一句话 Prompt

```
Wong Kar-wai cinematic: [describe subject]. high saturation red/green/blue, 
neo-noir low-key lighting, frame within a frame, foreground obstruction, 
wet street neon reflection, step-printing motion blur, film grain, handheld,
shallow depth of field, romantic melancholy, 1960s Hong Kong aesthetic
```

### 三大情绪快速切换

| 想要的感觉 | 加这段 |
|-----------|--------|
| **孤独冷感** | `cool blue-purple palette, off-center isolated figure, negative space, lone figure in neon city` |
| **暧昧暖感** | `warm amber tungsten glow, deep red silk, intimate close-up, slow motion longing` |
| **怀旧昏黄** | `sepia vintage filter, film grain, mirror reflection, faded memory, passage of time` |
