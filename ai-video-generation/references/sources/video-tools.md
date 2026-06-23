# 图生视频工具在AI短剧创作中的工作流

> 采集范围：从分镜图片/画面指令到可用视频片段的完整执行流程，覆盖可灵、即梦、Runway、Pika、海螺、Luma等主流图生视频工具。

---

## 0. 执行流程概览

AI短剧创作中图生视频的标准工作流：

1. **分镜设计**：用文生图工具（Midjourney/Stable Diffusion/即梦/可灵图片模型）生成关键帧画面。
2. **画面筛选**：选择构图清晰、主体明确、留有运动空间的高清图片。
3. **工具选择**：根据画面类型、时长需求、风格、预算选择图生视频工具。
4. **参数配置**：设置模型、时长、分辨率、运动强度、运镜方式、首尾帧等。
5. **Prompt编写**：描述动作/运动、镜头运动、氛围，避免重复描述画面已有内容。
6. **生成与迭代**：先生成测试版，满意后提升质量/分辨率，必要时续写或拼接。
7. **后期剪辑**：导入剪映/Premiere，调色、配音、加字幕、做转场。

---

# 方向1：可灵（Kling）图生视频

## 功能

可灵（Kling AI）是快手AI团队研发的多模态视频生成大模型。核心功能包括：

- **图生视频**：上传静态图片，让图中元素动起来。
- **文生视频**：输入文字描述生成视频。
- **首尾帧控制**：指定开始帧和结束帧，AI生成中间过渡。
- **动作控制**：上传参考视频驱动静态人物做出相同动作。
- **智能分镜**：3.0版本支持AI自动调度景别与机位，实现电影感叙事。
- **视频续写**：支持将视频延长至2-3分钟。
- **音画同步**：原生支持配音、音效、环境音、口型同步。
- **主体参考/数字演员**：多图或多视频参考，保持角色跨镜头一致性。

3.0系列模型矩阵：

| 模型 | 核心能力 | 适用场景 |
|---|---|---|
| 可灵视频3.0 | 智能分镜、15秒超长生成、原生音画同步 | 剧情短片、广告片、产品展示 |
| 可灵视频3.0 Omni | 主体参考、自定义分镜、角色一致性 | 系列内容、IP打造、多镜头叙事 |
| 可灵图片3.0 | 2K/4K超高清、光影真实感 | 海报、封面、概念图 |

## 参数设置

| 参数 | 可选项/范围 | 建议 |
|---|---|---|
| 模型 | 视频3.0 / 3.0 Omni / 2.6 / 2.1 | 3.0用于叙事，2.6用于带音频生成 |
| 时长 | 3-15秒（3.0）/ 5-10秒（2.x） | 先5-6秒测试，满意后续写 |
| 分辨率 | 最高1080p（Web），图片模型支持4K | 高品质模式用于最终输出 |
| 运动强度 | 全局运动系数0.3-3.0 | 2.2以下为安全上限，超过易触发防畸变降级 |
| 运动笔刷幅度 | 0.5-3.0+ | 2.5档为自然运动临界值，超过3.0易变形 |
| 模式 | 标准 / 高品质 / 专业 | 测试用标准，成片用高品质 |
| 宽高比 | 1:1, 16:9, 9:16, 4:3, 3:4, 3:2, 2:3, 21:9 | 根据平台选择 |
| 运动平滑度 | 开关 | 高系数下建议开启，避免帧间跳跃 |

## 运镜控制方式

1. **运动笔刷**：涂抹需运动区域，设置方向、强度（Proximity）、运动类型（位移/旋转/缩放）。
2. **全局运动系数**：在专业模式中调节整体运动强度。
3. **首尾帧控制**：通过两张图的像素差异反向推导运动轨迹。
4. **提示词嵌入**：在文本中写入运镜描述，如“镜头缓慢推进”“环绕跟拍”。
5. **专业模式自定义分镜（3.0 Omni）**：指定每个镜头的时长、景别、视角、运镜方式。

常用镜头指令：

| 中文 | 英文 | 效果 |
|---|---|---|
| 推镜头 | push in / dolly in | 向主体靠近，增强焦点 |
| 拉镜头 | pull out / dolly out | 远离主体，展现场景 |
| 左摇/右摇 | pan left / pan right | 水平旋转 |
| 上摇/下摇 | tilt up / tilt down | 垂直旋转 |
| 左移/右移 | truck left / truck right | 机位水平位移 |
| 跟拍 | tracking shot | 跟随移动主体 |
| 升降镜头 | crane up / crane down | 垂直升降 |
| 环绕 | orbit | 围绕主体旋转 |

## 优缺点

| 优点 | 缺点 |
|---|---|
| 中文提示词原生理解强 | 积分制，高频使用成本需核算 |
| 单段时长长（3.0最高15秒，2.x最高30秒） | 复杂场景下主体一致性偶有飘移 |
| 国内直连，无需代理 | 极致画质与Runway相比仍有差距 |
| 动作流畅、智能分镜、音画同步 | 有时提示词理解偏差，需多次重试 |
| 支持动作控制/数字演员绑定 | 精细动作（弹琴、书法）仍可能出错 |

## 适用场景

- 电影级短片、微短剧、广告片、产品展示
- 舞蹈/武术/动作模仿
- 角色一致性要求高的系列内容、IP短剧

## 示例Prompt

```
古装女子凭栏远眺，衣袂轻扬，镜头从远景缓慢推近至中景，
春日园林背景，柔和光线，电影质感，4K高清
```

```
[运动笔刷] 左侧裙摆随风缓慢右摆，幅度限制在15°内；
发丝末端轻微上扬，频率每秒0.7次
```

## 常见问题与解决

| 问题 | 原因 | 解决方案 |
|---|---|---|
| 画面崩坏 | 多主体复杂运动、矛盾风格词 | 每次只指定1-2个核心动态主体，避免“写实”与“卡通”混用 |
| 人物变形 | 运动幅度过大、缺少主体参考 | 运动笔刷幅度控制在2.5以内，使用图生视频+主体参考绑定角色 |
| 动作不自然 | 动作过于复杂、参考图质量低 | 使用参考视频驱动，拆分复杂动作为多个简单动作，上传高清参考图 |
| 提示词无效 | 描述太抽象或过长 | 使用“主体+动作+场景+光线+运镜+画质”结构，控制在80-120字符 |

---

# 方向2：即梦（Dreamina）图生视频

## 功能

即梦AI是字节跳动推出的AI视频生成工具，深度集成剪映生态。核心功能：

- **图片生视频**：上传单张或多张图片生成动态视频。
- **文本生视频**：文字直接生成视频。
- **首尾帧控制**：首帧和尾帧图片，AI生成中间过渡。
- **尾帧重复**：最后一帧重复显示，增强稳定性。
- **AI配乐**：自动生成背景音乐。
- **剪映协同**：生成素材可直接导入剪映精剪。

模型：视频S2.0（速度快）、视频S2.0 Pro（支持多镜头）。

## 参数设置

| 参数 | 可选项 | 建议 |
|---|---|---|
| 视频模型 | 视频S2.0 / S2.0 Pro | S2.0 Pro支持多镜头 |
| 时长 | 4秒 / 6秒 / 8秒等 | 6秒为标准长度 |
| 运镜 | 平移、旋转、推拉、缩放等 | 在提示词中明确方向 |
| 运动速度 | 多档可调 | 建议0.3-0.6，避免画面扭曲 |
| 模式 | 标准模式 / 流畅模式 | 标准均衡，流畅重画面流畅度 |
| 视频比例 | 16:9 / 9:16 / 1:1 | 抖音选9:16竖屏 |
| 使用尾帧 | 开关 | 开启增强稳定性 |
| 生成次数 | 1-4次 | 多次抽卡选最佳 |

## 运镜控制方式

- 预设运镜控制面板：选择平移、旋转、缩放等基础镜头运动。
- 首尾帧控制：上传首帧和尾帧，配合文字指令描述过渡动作。
- 提示词中嵌入运镜描述：如“镜头从左侧缓慢平移至右侧”“从近景环绕拉远”。

## 优缺点

| 优点 | 缺点 |
|---|---|
| 生成速度快 | 单段时长较短（最长8秒） |
| 中文提示词理解准确 | 画质上限1080p，顶尖商业级内容略显不足 |
| 与剪映生态深度协同 | 功能迭代快，部分高级功能稳定性待观察 |
| 免费额度对个人创作者基本够用 | 国际化场景和多语言支持有限 |
| 动漫/二次元风格表现好 | 长叙事内容需要多段拼接 |

## 适用场景

- 抖音/短视频快速出片
- 动漫风格、古诗词动画、二次元内容
- 已使用剪映的创作者工作流
- 自媒体文字稿转视频

## 示例Prompt

```
女孩在桃树下转身，长发随风飘动，镜头从近景环绕拉远，
花瓣缓缓飘落，3D动漫风格，动态模糊
```

```
少女撑油纸伞漫步，镜头从脚部特写抬升至全身，
樱花随风旋转飘落，日系滤镜，慢动作
```

## 提示词公式

```
[主体动作] + [场景变化] + [运镜控制] + [风格/特效]
```

技巧：每段指令控制在5秒内可实现的动作；避免抽象描述，如“唯美”改为“阳光透过树叶形成光斑”。

---

# 方向3：Runway Gen-3

## 功能

Runway是国际领先的AI视频生成平台，Gen-3 Alpha模型将视频生成时长提升至18秒，运动连贯性错误率较Gen-2下降76%。核心功能：

- **Text to Video**：文本生成视频。
- **Image to Video**：图像生成视频，Runway杀手级功能。
- **Motion Brush（运动笔刷）**：精确控制画面中特定区域的运动。
- **Camera Control**：指定镜头运动。
- **Extend**：在已生成视频基础上延长4-5秒。
- **Upscale**：高清化输出。
- **Fixed Seed**：固定种子值保持风格一致。

## 参数设置

| 参数 | 可选项 | 建议 |
|---|---|---|
| 模型 | Gen-3 Alpha / Alpha Turbo | Alpha Turbo用于快速测试 |
| 时长 | 4-18秒 | 4秒测试，10秒正式，18秒消耗最高 |
| 分辨率 | 1024×576（免费）/ 1920×1080（付费） | 成片用1080p |
| 运动强度 | 1-10 | 文生视频5-7，图生视频3-6 |
| 种子 | Fixed Seed | 保持系列视频风格一致 |
| 镜头运动 | 推/拉/摇/移/跟拍/升降/环绕/POV | 在提示词中指定或使用Camera Control |
| 生成次数 | 1-4个候选 | 多版本对比选择 |

## 运镜控制方式

1. **Camera Control**：直接输入镜头运动指令。
2. **Motion Brush**：涂抹区域并设置运动方向、强度、类型。
3. **提示词**：使用专业运镜英文描述。

常用镜头指令：

| 英文指令 | 效果 |
|---|---|
| slow zoom in / camera slowly pushes in | 缓慢推进，适合情绪/特写 |
| pan left to right / camera pans right | 横移，场景展示 |
| tracking shot following [subject] | 跟拍，角色移动 |
| overhead bird eye view / aerial shot | 俯视全景，宏大场景 |
| POV shot / first-person perspective | 第一人称，沉浸体验 |
| crane shot moving upward | 升降镜头，建筑/场景转换 |
| orbit around [subject] | 环绕主体 |

## 优缺点

| 优点 | 缺点 |
|---|---|
| 画质天花板，色彩过渡自然 | 需代理访问，国内网络稳定性影响体验 |
| 运镜控制精准，专业感强 | 成本较高，积分消耗大 |
| Motion Brush可实现精细区域控制 | 单段最长10-18秒，长视频需拼接 |
| 商业授权清晰，适合专业创作 | 中文prompt响应一般，建议用英文 |
| 与Midjourney、Adobe Premiere工作流完善 | 真实人脸生成有限制 |

## 适用场景

- 品牌广告、影视前期预可视化
- 专业短片、高质量B-roll
- 产品展示、概念演示
- 需要精细运动控制的画面

## 示例Prompt

```
A woman in an indigo dress stands in a cherry blossom forest in morning mist,
camera slowly pushes in to a close-up of her face, breeze gently moves her hair,
she looks into the distance with soft eyes, cinematic lighting, shallow depth of field, 8K, film grain
```

图生视频Prompt（只描述运动）：

```
Leaves sway gently, camera slowly pans right, morning light flows through leaf veins,
water surface ripples subtly
```

## 成本控制建议

- 先用标准质量测试，确认提示词有效后再用高质量。
- 使用Free Preview预览首帧，避免无效消耗。
- 优先关键场景用高质量，过渡场景用标准质量。

---

# 方向4：Pika Labs

## 功能

Pika Labs支持生成和编辑多种风格视频，包括3D动画、动漫、卡通、电影等。核心功能：

- **文生视频**：输入提示词生成视频。
- **图生视频**：上传图片生成视频。
- **文+图生视频**：结合文本与图片输入。
- **视频转视频**：上传视频进行风格化或修改。
- **Modify Region**：局部修改/替换视频中的区域。
- **Scene Ingredients（Pika 2.0）**：上传自定义图像（人物、产品、背景）融入AI生成场景。
- **Pikaffects（1.5）**：基于物理的视觉特效，如物体融化、爆炸。
- **Pikadditions / Pikaswaps（2.1+）**：插入或替换视频元素。

## 参数设置

| 参数 | 可选项 | 建议 |
|---|---|---|
| 版本 | 1.0 / 1.5 / 2.0 / 2.1 / 2.2 / 2.5 | 2.0+支持Scene Ingredients，2.5进一步提升质量 |
| 时长 | 3-10秒 | 社交媒体3-5秒 |
| 运动控制 | Motion Control + Strength | 值越大运动越大，但越容易变形 |
| 否定词 | 自定义 | 设置unwanted内容 |
| 种子值 | 固定 | 保持可复现性 |
| 文本一致性 | 参数调节 | 控制输出与提示词的匹配度 |
| 分辨率 | 1080p（付费） | 免费层分辨率较低 |
| 风格预设 | 3D动画/动漫/卡通/电影等 | 一键切换 |

## 运镜控制方式

- **Motion Control面板**：选择镜头运动方向（如推、拉、摇、移）。
- **Strength of motion**：调节运动幅度，值越大运动越剧烈。
- **Parameters面板**：设置否定词、种子、文本一致性。
- **Modify Region**：框选区域输入提示词进行局部修改（如“佩戴墨镜”）。
- **Scene Ingredients**：上传干净、光照良好的参考图，将人物/产品融入生成场景。

## 优缺点

| 优点 | 缺点 |
|---|---|
| 上手极快，界面极简 | 复杂运镜和精准动作控制较弱 |
| 风格效果多元，一键切换 | 需代理访问，国内体验受网络影响 |
| 局部编辑（Modify Region）强大 | 免费额度有限，重度使用需付费 |
| 短视频场景够用，适合Reels/抖音 | 单段时长较短 |
| 2.0+运动渲染更自然 | 专业创作场景受限 |

## 适用场景

- 社交媒体短视频、Reels、抖音切片
- 快速风格化内容、3D/动漫/卡通视频
- 产品局部修改、人物换装/换场景
- 零门槛快速出片

## 示例Prompt

```
A cyberpunk character walking through a neon-lit street at night,
camera tracking from behind, moderate motion, cinematic style, rain reflections on wet pavement
```

```
Upload product photo, Scene Ingredients: place the product on a minimalist white desk,
soft studio lighting, camera slowly orbits around showing all angles, clean commercial style
```

## 使用技巧

- 图生视频比文生视频更稳定，建议优先使用图生视频。
- 源图像越干净、背景越简单，Scene Ingredients融合效果越好。
- 运动强度建议从低到高测试，避免过大导致变形。

---

# 方向5：海螺视频（Hailuo AI / MiniMax）

## 功能

海螺AI（Hailuo AI）是MiniMax推出的AI视频生成工具，支持文生视频和图生视频。核心功能：

- **文生视频**：文字描述生成视频。
- **图生视频**：上传图片让画面动起来。
- **首尾帧**：上传首帧和尾帧，生成过渡视频。
- **参考图**：上传风格参考图指导生成风格。
- **T2V-01-Director模型**：支持结构化镜头指令控制运镜。
- 模型选择：Hailuo 2.3（综合质量最好）、Seedance 2.0（通用参考模式）。

## 参数设置

| 参数 | 可选项 | 建议 |
|---|---|---|
| 模型 | Hailuo 2.3 / Seedance 2.0 | 日常用2.3，风格化用Seedance 2.0+参考图 |
| 分辨率 | 480p / 768p / 1080p | 768p平衡，1080p最终成片 |
| 时长 | 5-10秒 | 6秒常用 |
| 生成数量 | 1-4条 | 先1条测试，满意后批量 |
| 参考图 | 支持 | 风格难描述时直接上传 |
| 运镜模板 | 15种预设 | 通过摄像机图标选择 |

## 运镜控制方式

海螺AI对自然语言运镜理解有限，建议使用**T2V-01-Director模型**的结构化镜头指令：

1. **预设运镜模板**：点击提示词框右下角摄像机图标，选择推/拉/摇/移/升降/环绕模板。
2. **直接嵌入镜头词**：在提示词中用方括号嵌入标准镜头词。

| 写法 | 示例 | 效果 |
|---|---|---|
| 并行触发 | `[推镜头,左移]` | 两种运动同步发生 |
| 分段触发 | `男子迈步向前[右移]。镜头抬升至肩部高度[上升]。` | 按顺序执行 |
| 单点强化 | `少女猛然抬头[上摇]` | 关键动作后触发镜头 |

标准镜头词列表：

| 中文 | 英文 | 含义 |
|---|---|---|
| [推镜头] | Push In | 机位沿光轴向前移动 |
| [拉镜头] | Pull Out | 机位沿光轴向后移动 |
| [左移] / [右移] | Truck Left / Truck Right | 机位水平位移 |
| [左摇] / [右摇] | Pan Left / Pan Right | 镜头水平旋转 |
| [上升] / [下降] | Crane Up / Crane Down | 垂直升降 |
| [环绕] | Orbit | 围绕主体旋转 |
| [变焦推进] | Zoom In | 光学变焦，非机位位移 |

## 优缺点

| 优点 | 缺点 |
|---|---|
| 免费额度慷慨，登录后每日配额充足 | 单段时长上限6-10秒，不适合长叙事 |
| 情绪质感强，人物表情和动作细腻 | 缺少精细运镜控制 |
| 风格化效果出众（电影感、赛博朋克、国风） | 4K/超高清场景略显不足 |
| 国内直连，速度快 | 纯中文描述偶尔理解不准确 |
| 运动流畅，不易明显形变 | 功能扩展性有限 |

## 适用场景

- 情绪短片、电影感短视频
- 产品动态展示、国风/赛博朋克风格
- 预算有限的创作者、自媒体
- 有参考图需要特定风格的场景

## 示例Prompt

```
雨夜街角，穿皮衣女子转身回眸，[推镜头]，霓虹灯光反射在湿漉地面，
电影感色调，慢动作，柔和灯光
```

```
一只橘猫在窗台上伸懒腰，阳光从侧面照进来，温馨治愈的氛围，慢动作
```

## 注意事项

- 必须选中**T2V-01-Director模型**才能识别镜头词。
- 同一时间点只能启用一个模板，多个模板会导致画面撕裂或卡顿。
- 禁用“提示词优化”开关，否则会自动改写原始镜头词导致失效。
- 负向提示中慎用“blurry”“out of focus”，否则变焦焦点过渡会被抑制。

---

# 方向6：Luma Dream Machine

## 功能

Luma Dream Machine支持文生视频和图生视频，以专业电影级镜头运动控制见长。核心功能：

- **Image-to-Video**：将静态图片转为动态视频。
- **Text-to-Video**：文字生成视频。
- **Camera Motion Control**：可视化镜头运动控制面板。
- **组合运动**：多种镜头运动组合。

## 参数设置

| 参数 | 建议 |
|---|---|
| 输入图片 | 清晰、静态的参考图，简单场景最佳 |
| 运动类型 | Push-in / Pull-out / Pan left/right / Move left/right / Orbit / Crane up/down |
| 时长 | 3-10秒 |
| 速度 | 产品展示慢速（8-10秒/圈），场景过渡快速（2-3秒） |
| 组合运动 | 基础+高级组合，留出2-3秒过渡 |

## 运镜控制方式

1. 在提示词框中输入 `camera` 调出镜头运动控制面板。
2. 选择可视化预览中的运动类型。
3. 支持直接嵌入镜头运动词：

| 运动类型 | 英文指令 | 建议时长 |
|---|---|---|
| 推进 | push-in | 3-4秒 |
| 拉远 | pull-out | 5-6秒 |
| 左右摇镜 | pan left / pan right | 3-5秒 |
| 左右平移 | move left / move right | 3-5秒 |
| 环绕 | orbit | 8-10秒 |
| 升降 | crane up / crane down | 4-5秒 |
| 组合运动 | combined movements | 3-10秒 |

## 优缺点

| 优点 | 缺点 |
|---|---|
| 专业cinematic效果，无需昂贵设备 | 复杂场景（含移动主体）效果不稳定 |
| 操作简单，输入camera即可调出面板 | 环绕镜头若速度/主体位置不当会显生硬 |
| 可视化预览，可预览运动效果 | 移动主体的场景需要多次尝试 |
| 运动类型丰富，支持组合 | 运动方向易产生歧义，需精确描述 |
| 支持文生和图生两种模式 | 过度复杂化会导致画面混乱 |

## 适用场景

- 建筑展示、风景、产品展示
- 静态场景动画、电影感空镜
- 需要专业镜头运动但缺少拍摄设备的场景

## 示例Prompt

```
Modern office desk with laptop and coffee cup, push-in camera motion,
soft morning light, cinematic depth of field
```

```
Smoothly push in toward the red vase over 4 seconds, revealing fine details,
soft natural lighting, shallow depth of field
```

```
Start with a medium shot of the product, add a slow orbit motion,
end with a gentle push-in to highlight details, clean commercial style
```

---

# 方向7：工具对比与选择

## 综合对比表

| 维度 | 可灵 | 即梦 | Runway Gen-3 | Pika 2.0 | 海螺 | Luma |
|---|---|---|---|---|---|---|
| **画质** | 高（最高4K/60fps） | 中（1080p） | 极高 | 中 | 中高 | 高 |
| **单段时长** | 15-30秒 | 5-8秒 | 10-18秒 | 4-10秒 | 6-10秒 | 3-10秒 |
| **中文支持** | 原生 | 原生 | 有限 | 有限 | 原生 | 有限 |
| **国内访问** | 直连 | 直连 | 需代理 | 需代理 | 直连 | 需代理 |
| **运镜控制** | 强（运动笔刷+全局系数+分镜） | 中 | 极强（Motion Brush+Camera Control） | 中 | 中（结构化镜头词） | 强（可视化面板） |
| **成本** | 中（积分制） | 低/免费 | 高（$15/月起） | 中 | 低/免费 | 中 |
| **生成速度** | 中等 | 快 | 中等 | 快 | 快 | 中等 |
| **强项** | 电影级画质、长叙事、智能分镜、动作控制 | 快速出片、剪映协同、动漫风格 | 画质天花板、运镜精细、商业授权 | 上手快、风格多、局部编辑 | 免费额度、情绪质感、风格化 | 静态场景、建筑风景、产品 |
| **弱项** | 积分成本、复杂一致性 | 画质上限、时长短 | 需代理、成本高 | 复杂控制弱、时长短 | 时长短、精细控制弱 | 动态主体不稳定 |
| **适合场景** | 微短剧、广告、产品、动作模仿 | 抖音/短视频、动漫、自媒体 | 品牌广告、影视预演、专业短片 | 社交媒体、快速风格化 | 情绪短片、电影感、免费创作 | 建筑、风景、产品展示 |

## 成本/速度/可控性对比

| 工具 | 免费额度 | 付费起步 | 生成速度 | 可控性 |
|---|---|---|---|---|
| 可灵 | 有，有限 | 积分制 | 中等 | 高 |
| 即梦 | 每日60-100积分 | 免费/订阅 | 快 | 中 |
| Runway | 125积分/月 | $15/月 | 中等 | 极高 |
| Pika | 30积分/3视频 | $10/月 | 快 | 中 |
| 海螺 | 免费额度慷慨 | $9.99/月 | 快 | 中 |
| Luma | 有免费额度 | 订阅/按量 | 中等 | 中高 |

## 选择建议

- **影视从业者、品牌视频创作者**（追求画质和运镜）：首选 **Runway Gen-3 Alpha**，搭配英文prompt。
- **国内视频创作者、微短剧**（需要长时长、中文描述）：选 **可灵 AI**，30秒时长优势无可替代。
- **社交媒体运营、短视频博主**（快速出片、风格多样）：选 **Pika 2.0**（需接受代理）或 **即梦视频**。
- **预算有限、想免费创作**（电影感风格）：选 **海螺 AI**。
- **深度依赖剪映剪辑**：选 **即梦视频**，生态协同效率最高。
- **建筑/风景/产品展示**：选 **Luma Dream Machine**。
- **全都要且预算充足**：国内场景用 **可灵**，顶尖质感切换 **Runway**，两者互补。

---

# 方向8：提示词语法

## 图生视频提示词结构

```
[主体] + [动作/运动] + [场景] + [镜头运动] + [氛围/风格] + [时长/质量]
```

与图像提示词的关键差异：视频prompt必须描述**随时间变化的运动**，而不是静态画面。

| 类型 | 图像Prompt | 视频Prompt |
|---|---|---|
| 静态vs动态 | A woman standing in rain | A woman stands still as rain begins to fall, drops splashing on her umbrella, she slowly looks up |

## 关键要素与写法

| 要素 | 写法 | 示例 |
|---|---|---|
| 主体 | 明确外貌、服饰、姿态 | 穿米色风衣的女性 |
| 动作 | 具体动词+方向+速度 | 缓缓转身望向镜头 |
| 场景 | 环境+光线+时间 | 秋日落叶街道，午后暖阳透过树枝 |
| 镜头运动 | 推/拉/摇/移/环绕/跟拍 | 镜头从侧面跟拍 |
| 速度 | 慢/快速/逐渐/突然 | 慢动作，逐渐加速 |
| 风格 | 电影感/日系/赛博朋克/写实 | 电影感色调，35mm胶片颗粒 |
| 质量 | 分辨率/帧率/光影 | 4K高清，柔和光线 |
| 连续性 | 保持稳定元素 | 保持人物服装、脸型、构图一致 |

## 动作描述技巧

将模糊动词替换为具体描述：

| 模糊 | 具体 |
|---|---|
| Moving | Gliding smoothly forward |
| Walking | Striding confidently with purpose |
| Falling | Drifting down gently like a feather |
| Running | Sprinting at full speed, feet pounding |

运动关键词：

- **速度**：slowly, quickly, gradually, suddenly, gently
- **方向**：forward, backward, upward, spiraling, circling
- **质量**：smoothly, jerkily, gracefully, heavily, lightly
- **强度**：subtly, dramatically, explosively, delicately

## 镜头运动关键词

| 中文 | 英文 | 含义 |
|---|---|---|
| 推镜 | Push in / Dolly in | 机位靠近主体 |
| 拉镜 | Pull back / Dolly out | 机位远离主体 |
| 左摇 | Pan left | 镜头水平左转 |
| 右摇 | Pan right | 镜头水平右转 |
| 上摇 | Tilt up | 镜头垂直上转 |
| 下摇 | Tilt down | 镜头垂直下转 |
| 跟拍 | Tracking shot | 跟随移动主体 |
| 升降 | Crane shot | 垂直升降 |
| 环绕 | Orbit | 围绕主体旋转 |
| 手持 | Handheld | 轻微自然晃动 |
| 静态 | Static | 镜头不动 |

## 时间语言

使用顺序词描述时间变化：

- First... then... finally...
- As... while...
- Beginning with... transitioning to...
- Starting from... ending with...

示例：

```
The scene begins with an empty room, sunlight slowly filling the space through the window.
As the light reaches the center, a flower gradually blooms, petals unfurling one by one.
```

## 图生视频特别提示

图生视频的Prompt应重点描述**“怎么动”**，而不是“画面长什么样”：

- ✅ 正确：`The woman slowly turns her head toward camera, hair gently moving in the breeze, soft smile forming on her face`
- ❌ 错误：`A beautiful woman with long brown hair wearing a blue dress`（这些信息已在图片中呈现）

### 适合的图生视频素材

- ✅ 主体清晰、构图留有运动空间
- ✅ 主体姿态适合动起来
- ✅ 具备自然运动潜力的元素：水、布料、头发、烟雾、云层

### 不建议的素材

- ❌ 非常正式、静态的构图
- ❌ 主体贴近边缘，没有运动空间
- ❌ 元素过多、场景过复杂
- ❌ 过度风格化图片（可能不好动画化）

## 负面提示词建议

```
变形, 扭曲, 模糊, 人物崩坏, 肢体异常, 画面抖动, 不自然,
多余的手指, 面部变形, 运动残影, 果冻效应, 镜头漂移
```

注：Runway Gen-4官方建议**描述应该发生什么**，而不是罗列不应该发生什么。但其他工具（如Stable Diffusion视频模型）负面提示词仍然有效。

## 常见错误与修正

| 错误类型 | 错误示例 | 修正示例 |
|---|---|---|
| 太静态 | A city at night with lights | City skyline at night, cars streaming by below, lights twinkling, clouds slowly drifting past the moon, time-lapse feel |
| 太复杂 | A person walks into a room, picks up a book, reads it, puts it down, walks to window, opens it... | A person enters a sunlit room, pauses by the window, gazing thoughtfully outside, curtains gently swaying in the breeze |
| 运动冲突 | Camera zooms in while pulling back, subject runs left while moving right | Smooth dolly in toward the subject, who walks slowly toward camera |
| 抽象描述 | 一个好看的风景 | 夕阳下的撒哈拉沙漠，金色沙丘连绵起伏，一只骆驼队缓缓走过，光影斑驳 |

## 模型差异提示

| 工具 | 特点 | 提示词建议 |
|---|---|---|
| 可灵 | 人类动作强，复杂场景稳定，可描述表情 | 中文描述，突出动作和表情细节 |
| Runway | 电影级质感，Motion Brush精细 | 英文优先，强调镜头运动和光影 |
| 即梦 | 中文理解好，动漫风格强 | 中文描述，适合二次元/动漫 |
| 海螺 | 情绪质感好，风格化强 | 加入情绪词，使用结构化镜头词 |
| Pika | 风格化强，适合社交媒体 | 简洁明确，多用风格词 |
| Luma | 静态场景运镜佳 | 强调camera运动类型和时长 |

## 示例Prompt模板

### 产品展示

```
[Product] rotating slowly on [surface], [lighting type],
camera orbits smoothly showing all angles, [style], commercial quality, clean and professional
```

示例：

```
Luxury perfume bottle rotating slowly on black marble,
dramatic rim lighting with soft reflections,
camera orbits smoothly showing all angles, high-end commercial quality, elegant and sophisticated
```

### 生活方式/短剧

```
[Person] [action] in [setting], [time of day], [camera movement],
[mood], lifestyle video, natural and authentic
```

示例：

```
Young couple walking hand in hand along the beach, golden hour sunset,
camera tracking alongside them, romantic and peaceful mood, lifestyle video, warm color grading
```

### 短剧分镜（中文）

```
[角色]在[场景]中[动作]，镜头[运动方式]，[光线]，[情绪]，电影质感，4K
```

示例：

```
古装女子在庭院中缓缓转身，镜头从背后推近至侧脸特写，
月光洒落，清冷孤独，电影质感，4K高清
```

### 抽象/艺术

```
[Visual elements] [motion description], [color palette], [style],
abstract and artistic, [mood/feeling]
```

示例：

```
Flowing ink drops dispersing in water, swirling and mixing in slow motion,
deep blues and golds, abstract and artistic, mesmerizing and meditative, macro photography style
```

---

# 引用来源

1. 可灵全攻略：从新手到高手，2026 AI视频创作实战指南
   - https://www.toutiao.com/article/7615439294294999587/

2. 可灵3.0 Kling AI 官方能力介绍（智能分镜、音画同步、15秒超长生成）
   - https://klingapi.com/zh

3. 可灵ai图生视频怎么控制幅度：运动笔刷、全局系数、首尾帧、提示词限定
   - https://www.php.cn/faq/2124934.html

4. 即梦AI详细文生图&文生视频教程（S2.0、提示词公式、剪映协同）
   - https://www.toutiao.com/article/7477189499131265571/

5. 即梦ai怎么制作短视频（图片生视频参数、运镜、运动速度、尾帧）
   - https://product.pconline.com.cn/itbk/top/qa/1879/18790427.html

6. Runway Gen-3 Alpha视频生成教程：从零基础到专业级创作
   - https://aitoolsnav.cn/2163.html

7. AI视频生成神器——Pika Labs详细操作教程（1.0/图生视频/Modify Region）
   - https://zhuanlan.zhihu.com/p/684165169

8. Pika 2.0: Scene Ingredients 与 AI 视频升级
   - https://morphic.com/zh/ai-glossary/Pika-20

9. 海螺 AI 新手教程：图生视频、参考图、运镜模板选择
   - https://www.aidiscover.cn/articles/hailuo-ai

10. 海螺AI提示词怎么指定镜头运动：推拉摇移运镜指令详解
    - https://www.ufcn.cn/article/2412468.html

11. How To Control Camera Motion In Luma Labs Dream Machine
    - https://blog.segmind.com/how-to-control-camera-motion-in-luma-labs-dream-machine/

12. AI 视频生成工具横评：Runway、可灵、Pika、海螺 AI、即梦 2026
    - https://www.uuaihub.com/blog/ai-video-tools-2026

13. 视频提示词（Video Prompting）：结构、动作、镜头、时间、风格
    - https://armox.ai/zh/academy/prompt-video

14. AI Video Prompts: Scripts, Scenes, Camera Moves and Motion
    - https://gptprompts.ai/ai-video-prompts
