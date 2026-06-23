# 真人写实 Prompt 工程蒸馏

> 来源：即梦AI官方教程 + Midjourney真人照片公式 + 实战经验
> 采集日期：2026-06-24

## 核心公式

### 即梦真人公式（ChooseAI）
```
人物基础信息 + 五官细节 + 穿搭妆容 + 动作神态 + 场景环境 + 风格参数
```

### Midjourney真人公式（CSDN）
```
Photography Theme + Image Content + Image Angle + Image Focus + Lighting + Weather/Time + Camera/Film + Realism Descriptors + Aspect Ratio + --style raw --stylize 0
```

## 皮肤/质感关键词库

### 皮肤真实感（PHP.cn即梦教程）
- visible pores on nose and forehead
- faint freckles under natural light
- subtle sebum sheen on T-zone
- translucent skin showing faint blue subdermal veins on temple
- natural lip texture with vertical lines
- natural asymmetry in eyebrow arch and eyelid crease

### 材质真实感
- realistic fabric drape with micro-wrinkles and fiber fuzz on cotton
- condensation droplets on ceramic mug
- subtle reflection on eyeglass lenses
- accurate caustic light pattern on lens

## 真人身份锚点

- slightly tousled hair from removing headphones
- one earbud still in left ear
- holding a matte-finish ceramic mug, steam rising
- wearing prescription glasses with thin titanium frame

## 反风格化关键词（--no / 负面提示）

即梦/Midjourney通用：
```
--no illustration, painting, cartoon, anime, 3D render, CGI, sketch, drawing, oversaturated, plastic skin, smooth gradient, airbrushed, perfect symmetry, cloned features
```

## 分层写实增强

1. 基础层：photorealistic, DSLR photograph, shot on Kodak Portra 400
2. 中间层：subsurface scattering on ears, accurate occlusion shadow under chin
3. 顶层：photographic evidence quality, forensic-level detail, consistent light direction

## 4场景真人模板（即梦Seedance 2.0实测）

### 日常写真
22岁亚洲男生，圆脸，双眼皮，黑色短发，额前碎刘海，皮肤白皙带轻微痘印，黑色连帽卫衣+灰色运动裤+白色运动鞋，双手插卫衣口袋，站姿放松微微低头浅笑，背景深秋银杏道金黄落叶，暖调3500K光线轻微柔焦，高清8K保留皮肤纹理发丝细节无过度磨皮

### 古风真人
28岁中国古风女子，柳叶眉杏眼樱桃小嘴，清透底妆，高颅顶盘发插玉簪，淡青色齐胸襦裙裙摆暗纹荷花，外披薄纱披风，手持团扇站姿优雅微微侧身，背景中式庭院假山荷花池青瓦白墙，高清8K保留襦裙暗纹玉簪纹理皮肤通透无过度磨皮

### 职场真人
32岁职场男性，方形脸浓眉大眼鼻梁高挺，短发利落无刘海，深灰色西装+白色衬衫+黑色领带，佩戴黑色商务手表，站姿挺拔面带微笑眼神专业，背景现代简约办公室办公桌电脑绿植，正面平视镜头高清8K保留西装纹理皮肤质感自然

### 短视频真人（适配抖音）
20岁大学生女生，圆脸双眼皮，元气妆容橘色眼影豆沙色口红，高马尾发尾蓬松，白色oversize T恤+黑色工装裤+白色板鞋，在校园林荫道行走双手自然摆动笑容灿烂，0.8x慢跟拍轻微呼吸晃动，竖屏9:16轻微颗粒感增强真实感
