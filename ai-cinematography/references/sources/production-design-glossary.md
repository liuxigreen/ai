# 电影工业级场景/道具/材质描述词库

> 来源：FilmDaft Set Dressing指南 + Art Department Glossary(80+术语) + FilmFarm Distressing技法
> 蒸馏日期：2026-06-24

## 道具三级分类体系

| 层级 | 英文 | 定义 | AI Prompt中的应用 |
|------|------|------|-----------------|
| **手持道具** | Hand Props | 演员手持或直接接触的物品（手机、餐具、枪支） | 特写镜头必须写清材质+磨损+反光特性 |
| **场景道具** | Set Props | 场景中的大型物品（家具、灯具、车辆），演员不操作但构成场景主体 | 中景写清材质老化+摆放逻辑 |
| **陈设道具** | Set Dressing / Smalls | 装饰性小物品（书籍、花瓶、相框、烟灰缸） | 全景写清层次+疏密节奏 |

## 材质老化/磨损词库（按材料分类）

### 金属（Metal）
| 老化类型 | 视觉特征 | Prompt关键词 |
|---------|---------|-------------|
| 锈蚀 | 橙褐色斑点/片状剥落/边缘腐蚀 | rusted iron surface, orange-brown oxidation spots, flaking rust at edges, pitted corrosion |
| 刮擦 | 表面细线/深划痕/露底金属光泽 | scratched stainless steel, fine surface scratches catching light, deeper gouges revealing raw metal |
| 铜绿 | 蓝绿色粉状氧化层（铜/青铜专用） | verdigris patina on bronze, blue-green oxidation powder, weathered copper with turquoise staining |
| 指纹/油污 | 表面哑光斑块 | fingerprint smudges on polished metal, oil residue darkening around edges and handles |
| 暗沉 | 失光/均匀暗哑 | tarnished silver, dulled chrome finish, loss of specular highlight on worn brass |

### 木材（Wood）
| 老化类型 | 视觉特征 | Prompt关键词 |
|---------|---------|-------------|
| 开裂 | 沿纹理的纵向裂口 | cracked wood along grain lines, splitting at edges, visible fissures exposing raw interior |
| 剥落 | 漆面/饰面片状脱落 | peeling varnish exposing bare weathered wood, flaking paint revealing previous layers |
| 碰撞痕迹 | 边角凹陷/磕碰坑 | dented corners, impact hollows, chipped edges on wooden furniture |
| 水渍 | 环形白迹/发黑 | water ring stains on table surface, dark moisture marks along base, warped veneer from water damage |
| 磨损 | 常接触处木纹发亮 | worn armrests with polished wood grain from years of use, foot-scuffed chair legs, table edge burnished by elbows |

### 皮革（Leather）
| 老化类型 | 视觉特征 | Prompt关键词 |
|---------|---------|-------------|
| 裂纹 | 表面细密龟裂 | cracked leather with fine crazing pattern, deep creases at flex points |
| 磨损 | 边角露底/颜色变浅 | worn leather edges showing lighter base color, scuffed corners on leather briefcase |
| 褶皱 | 使用痕迹的深褶 | deep natural creases from repeated use, crushed leather patina on seat cushions |
| 褪色 | 受光照区域色差 | sun-faded leather with color gradient, UV-bleached patch on exposed side |

### 布料/织物（Fabric）
| 老化类型 | 视觉特征 | Prompt关键词 |
|---------|---------|-------------|
| 褪色 | 整体/局部颜色变淡 | sun-bleached cotton with uneven fading, washed-out color on frequently exposed areas |
| 起球 | 表面纤维小球 | pilled wool sweater surface, tiny fiber balls on high-friction areas |
| 磨破 | 边缘/膝肘部破损 | frayed cuffs on cotton shirt, threadbare at elbows, distressed denim with hole developing at knee |
| 污渍 | 油渍/茶渍/墨渍局部染色 | coffee stain ring on tablecloth, ink blot bleeding into fabric fibers, grease spot darkened on cotton |

### 玻璃/陶瓷（Glass/Ceramic）
| 老化类型 | 视觉特征 | Prompt关键词 |
|---------|---------|-------------|
| 裂纹 | 釉面细纹（陶瓷） | crazed ceramic glaze with fine network of cracks, hairline fracture in porcelain |
| 缺口 | 边缘小豁口 | chipped rim on ceramic mug, small notch missing from plate edge |
| 冷凝水 | 水珠附着 | condensation droplets on cold glass surface, beads of moisture running down chilled bottle |
| 指纹 | 油性印记 | greasy fingerprints on drinking glass, smudged rim from lip contact |

### 纸张/印刷品（Paper）
| 老化类型 | 视觉特征 | Prompt关键词 |
|---------|---------|-------------|
| 泛黄 | 边缘/整张变黄 | yellowed paper edges, age-toned newsprint, foxing spots on old book pages |
| 折痕 | 折叠线/展开痕迹 | crease marks from being folded, dog-eared corners, flattened fold lines |
| 卷边 | 边缘翘起 | curled paper edges from humidity, rolled corners on old poster |
| 撕裂 | 不规则裂口 | torn paper edge with irregular fiber tear, partial rip from staple removal |

## Set Dressing层次构建法（工业级）

### 层次顺序（从大到小）
```
第1层：大型家具（Furniture） → 建立空间功能和时代
第2层：中型陈设（Dressing） → 帷幔/灯具/地毯/电器
第3层：小型物品（Smalls） → 书籍/餐具/洗漱用品/个人物品
第4层：表面细化（Top Dressing） → 灰尘/划痕/指纹/水渍
```

### 每层的AI Prompt注入方式

**第1层示例**：
```
Space defined by [furniture item] with [material + aging]. 
A worn mahogany executive desk with decades of use polished into the armrests.
```

**第4层示例**：
```
Surface dressed with [smalls] revealing character. 
Desk scattered with: half-empty coffee mug(stale ring underneath), 
crumpled sticky notes, a framed photo face-down, 
pencil shavings near keyboard.
```

## 关键术语速查（AI Prompt直接引用）

| 术语 | 含义 | Prompt用法 |
|------|------|----------|
| Hero Prop | 特写级道具，必须经得起近距离审视 | 标为Hero的物品写3倍细节 |
| Practical | 真正可用的（水龙头真出水/灯真亮） | 光源加"practical lamp casting warm glow" |
| Patina | 长期使用形成的自然老化层 | "natural patina of age on brass doorknob" |
| Lived-in | 有人住过的痕迹感 | "lived-in apartment, not staged, real signs of daily life" |
| Weathered | 风吹日晒导致的自然老化 | "weathered wooden fence, sun-bleached and rain-stained" |
| Worn | 频繁使用导致的磨损 | "worn leather chair with cracked armrests from years of use" |
| Dusty | 灰尘覆盖 | "thin layer of dust on unused shelf, undisturbed except for one removed object" |
| Grimy | 油污/积垢 | "grimy kitchen tiles behind stove, years of cooking residue" |

## 场景可信度检查清单

每条Prompt生成前自查：
- [ ] 所有物品有"使用痕迹"吗？（全新=假）
- [ ] 光线有来源吗？（Practical lights count）
- [ ] 人物和环境有互动证据吗？（桌子上的杯子有人喝过）
- [ ] 物品摆放符合角色习惯吗？（整洁/邋遢/强迫症/随意）
- [ ] 有一个观众第一遍不会注意但第二遍恍然大悟的隐藏细节吗？
